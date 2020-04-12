
#include<stdio.h>
int main()
{
int i,n,p[10]={1,2,3,4,5,6,7,8,9,10},min,k=1,btime=0;
int burst_time[10],temp,j,arrival_time[10],wt[10],tt[10],ta=0,sum=0;
float wavg=0,tavg=0,tsum=0,wsum=0;
printf(" *******Shortest Job First Scheduling*******\n");
printf("\nEnter total No. of processes :");
scanf("%d",&n);

// taking input about the arrival time and the burst time
for(i=0;i<n;i++)
{
printf("\tEnter the arrival time of %d process :",i+1);
scanf(" %d",&arrival_time[i]);
printf("\tEnter the burst time of %d process :",i+1);
scanf(" %d",&burst_time[i]);
}

// Sorting process based on the arrival time
for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
{
if(arrival_time[i]<arrival_time[j])
{
temp=p[j];
p[j]=p[i];
p[i]=temp;
temp=arrival_time[j];
arrival_time[j]=arrival_time[i];
arrival_time[i]=temp;
temp=burst_time[j];
burst_time[j]=burst_time[i];
burst_time[i]=temp;
}
}
}

int priority(int arr_t,int bur_t,int total_t)
{
    if(arr_t > total_t)
    {
        return 0;
    }
    else
    {
    int waiting_time = total_t - arr_t;
    return 1+(waiting_time/bur_t);
    }
}

for(j=0;j<n;j++)
{
btime=btime+burst_timetime[j];
min=priority(arrival_time[k],burst_time[k],btime);
for(i=k;i<n;i++)
{
if (btime>=arrival_time[i] && priority(arrival_time[i],burst_time[i], btime) > min)
{
temp=p[k];
p[k]=p[i];
p[i]=temp;
temp=arrival_time[k];
arrival_time[k]=arrival_time[i];
arrival_time[i]=temp;
temp=burst_time[k];
burst_time[k]=burst_time[i];
burst_time[i]=temp;
}
}
k++;
}
wt[0]=0;
for(i=1;i<n;i++)
{
sum=sum+burst_time[i-1];
wt[i]=sum-arrival_time[i];
wsum=wsum+wt[i];
}
wavg=(wsum/n);
for(i=0;i<n;i++)
{
ta=ta+burst_time[i];
tt[i]=ta-arrival_time[i];
tsum=tsum+tt[i];
}

tavg=(tsum/n);

printf("********");
printf("\n RESULT:-");
printf("\nProcess\t Burst\t Arrival\t Waiting\t Turn-around" );
for(i=0;i<n;i++)
{
printf("\n p%d\t %d\t %d\t\t %d\t\t\t%d",p[i],burst_time[i],arrival_time[i],wt[i],tt[i]);
}

printf("\n\nAVERAGE WAITING TIME : %f",wavg);
printf("\nAVERAGE TURN AROUND TIME : %f",tavg);
return 0;
}
