---
title: "Ubuntu Performance Slower"
date: 2011-08-02
forum: General Help
---

### Post by Moneyfreak on 2011-08-02
Hi

I find that for some strange reason the performance of Ubuntu is slower than that of RHEL 5.0.

This being that Ubuntu is running on a superior hardware 64-bit.

Code :
[HTML]
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
#include<time.h>
#include <errno.h>

int flag;
long total_request, actual_request;
time_t strtime, etime, curtime;
static pthread_mutex_t check_mutex;
FILE *fp;

void *cwt_testing( void );

int main(int argc, char *argv[] )
{
    int x,k;
    long j = 0, a = 0;  
    flag = 1;

    if (argc < 3)
    {   
        printf ("%s <Concurrent Threads> <TimeOfExecution (s)>\n", argv [0]) ;
        return 1 ; 
    }   

    x = atoi(argv[1]);
    actual_request = 0;
    a = atol(argv[2]);
    
    fp = fopen ("error","a+");
    pthread_mutex_init(&check_mutex,NULL);
    
    pthread_t pthread1[x];
    char *str_time = NULL ;
    int iRet1;
    time_t tt = 0, tt1 = 0, tt2 = 0;  

    tt = time(NULL);
    str_time = ctime(&tt) ;
    strtime = tt ;
    etime = a;
    curtime = 0;
    printf ("START Time :: [%s]\n", str_time) ;

    for(k=0; k< x ; k++)
    {   
        iRet1 = pthread_create ( &pthread1[k], NULL, (void*)cwt_testing, NULL);
        if( iRet1 != 0 ) 
        {
            fprintf(fp, "Thread creation failed: %s\n", strerror(errno));  
        }
    }   
    for(k=0; k< x ; k++)
    {
        pthread_join( pthread1[k], NULL );
    }

    printf ("START Time :: [%s]\n", str_time) ;
    printf ("START Time :: [%ld]\n", tt) ;
    tt1 = tt ;

    tt = time(NULL) ;
    str_time = ctime(&tt) ;
    printf ("END time :: [%s]\n", str_time) ;
    printf ("End Time :: [%ld]\n", tt) ;
    printf("Total Number of request [%ld]\n", actual_request) ;
    printf ("Time taken :: [%ld]\n",tt - tt1) ;
    printf ("Request per sec :: [%ld]\n",actual_request / (tt - tt1-1)) ;
    exit(0);

}


void *cwt_testing()
{
    while(flag)
    {
        pthread_mutex_lock(&check_mutex);
        actual_request ++;
        if (((curtime = time(NULL))-strtime) >= etime )
        {
            flag = 0;
            break;
        }
        pthread_mutex_unlock(&check_mutex);
        printf ("\nThread");
    }
    printf ("\nFILE:LINE:: [%s:%d]\n", __FILE__, __LINE__);

}
[/HTML]Complie Option:
[HTML]
gcc -o thread <filename> -lpthread
[/HTML]Execute Code :
[HTML]
./thread 100 60
[/HTML]Result : 
[HTML]
Ubuntu [Requests per second] : 69433
RHEL  [Requests per second]  : 111286
[/HTML]Should i change some setting in Ubuntu to achive better results ?

Thanks

---

