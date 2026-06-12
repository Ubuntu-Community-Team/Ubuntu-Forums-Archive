---
title: "Thread Throughput problem"
date: 2011-08-01
forum: General Help
---

### Post by Moneyfreak on 2011-08-01
Hi all,

I have a thread creation program in C.
I just wanted to know the throughput ie number of request processed per second.

I found that its way more slower on Ubuntu then in red hat 5.0

Even more interesting fact is that Ubuntu is 64-bit with a better processor.

Is there some kind of setting that i have to change to get a better throughput ?
HELP !!!

Thanks

---

### Post by blind2314 on 2011-08-01
> **Moneyfreak said:**
> Hi all,
 
I have a thread creation program in C.
I just wanted to know the throughput ie number of request processed per second.
 
I found that its way more slower on Ubuntu then in red hat 5.0
 
Even more interesting fact is that Ubuntu is 64-bit with a better processor.
 
Is there some kind of setting that i have to change to get a better throughput ?
HELP !!!
 
Thanks
 
Did you use the same compiler on each OS, with the same flags? I have a hard time believing that it is "way more slower" on Ubuntu, unless something changed at compilation time. Also, the second is not the default time slice of the CPU, so you're going to have to do a bit of "voodoo" to get the human readable answer (requests per second) that you're after.
 
Maybe post a bit of code that shows what you've done so far?

---

### Post by Moneyfreak on 2011-08-01
> **blind2314 said:**
> Did you use the same compiler on each OS, with the same flags? I have a hard time believing that it is "way more slower" on Ubuntu, unless something changed at compilation time. Also, the second is not the default time slice of the CPU, so you're going to have to do a bit of "voodoo" to get the human readable answer (requests per second) that you're after.
 
Maybe post a bit of code that shows what you've done so far?


Here is the gist of my code.
Tried running on redhat and ubuntu
./a.out 100 10
Red Hat [Requests per second] : 111286
Ubuntu [Requests per second] :  69443

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

[/HTML]

---

### Post by Moneyfreak on 2011-08-02
Any clues ???

Please HELP !!!

---

