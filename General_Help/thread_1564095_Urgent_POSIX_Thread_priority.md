---
title: "Urgent: POSIX Thread priority"
date: 2010-08-30
forum: General Help
---

### Post by Amit_Oza on 2010-08-30
Hi all,
 
I have increased the priority of main in main itself(Priority is raised to 99). After that I am trying to create a thread from a function "CreateThreadZero". As per my expectations, as main has maximum priority, this thread should be put to run only after I lower the priority of main. The same works perfectly fine if I create the thread 0 from main instaed of a sub-function. Why is it so? A sub-function called from a thread should be executed with the thread priority of calling thread. Please let me know is my understanding correct?
 
Code Snippet:
---------------------------------------------------------------
int main(void)
{
  int main_policy;
  struct sched_param main_param;
  
  main_policy = SCHED_FIFO;
  main_param.sched_priority = 99;
  pthread_setschedparam(pthread_self(), main_policy, &main_param);
 
  printf("I am In MAIN Thread");
  CreateThreadZero();
  printf("Created thread zero");
  main_param.sched_priority = 1;
  pthread_setschedparam(pthread_self(), main_policy, &main_param);
}
 
void CreateThreadZero(void)
{
  pthread_create(&ThreadId0, &ThreadAttribute0,  *ThreadBody0, NULL);
}
 
void ThreadBody0(void)
{
  printf("In thread body 0");
  pthread_exit(NULL);
}
 
-------------------------
OUTPUT:
------------------------
I am In MAIN Thread
In thread body 0
Created thread zero
 
***************************************************************
***************************************************************
 
[COLOR=red]Now, thread zero is directly called from main instead of sub-function[/COLOR]
 
 
int main(void)
{
  int main_policy;
  struct sched_param main_param;
  
  main_policy = SCHED_FIFO;
  main_param.sched_priority = 99;
  pthread_setschedparam(pthread_self(), main_policy, &main_param);
 
  printf("I am In MAIN Thread");
  pthread_create(&ThreadId0, &ThreadAttribute0,  *ThreadBody0, NULL);
  printf("Created thread zero");
  main_param.sched_priority = 1;
  pthread_setschedparam(pthread_self(), main_policy, &main_param);
}
 
void ThreadBody0(void)
{
  printf("In thread body 0");
  pthread_exit(NULL);
}
 
-------------------------
OUTPUT:
------------------------
I am In MAIN Thread
Created thread zero
In thread body 0

---

### Post by meoconvn38 on 2010-08-30
I saw no different between these code. And Please notice, when you change the priority, the system will wait until the thread with higher priority finished then it's can take effect.
:popcorn:

---

### Post by Amit_Oza on 2010-08-30
The change is the main body. In the first snippet,  
 
*********************************************
------
printf("I am In MAIN Thread");
[COLOR=red]CreateThreadZero();[/COLOR]
printf("Created thread zero");
-----
********************************************
 
 
In the second snippet:
********************************************
---------
printf("I am In MAIN Thread");
[COLOR=red]pthread_create(&ThreadId0, &ThreadAttribute0, *ThreadBody0, NULL);[/COLOR]
printf("Created thread zero");
-------

---

### Post by lisati on 2010-08-30
Formatting suggestion: begin your code snippet with the [noparse]```
 tag and end it with the 
```[/noparse] tag.

---

### Post by Amit_Oza on 2010-08-30
Thnx for the info on tags. Will take care now onwards:D.

---

### Post by Amit_Oza on 2010-08-30
Requesting for your kind help to clarify the matter. 
 :confused:

---

### Post by ean5533 on 2010-08-30
Disclaimer: I'm not an expert in concurrent programming, so I COULD be mistaken about the following. However, I'm 95% sure I'm correct.

Setting thread priority does not guarantee execution order. Even if you set the main thread's priority to the max, you are not explicitly setting the thread schedule. Priorities are more like suggestions -- suggestions which the kernel takes into account while it handles actually scheduling the threads. You can try and use stuff like thr_yield(void), but you still aren't promised to get what you want.

Now, as far as why you're getting different results between creating the thread directly and creating it in a sub-function, I think that's just a coincidence. I'm betting if you ran the two programs enough times, you'd eventually see the results flip-flop. The only difference between those two examples is that in the second example the main thread has extra work to do with cleaning up its call to CreateThreadZero(). In other words, it has to do more stuff, giving that second spawned thread a greater chance of being executed before main finishes.

Instead of trying to force threads to execute in the order you want, you should either try keeping things in one thread or redesigning your program in such a way that it doesn't matter what order the threads execute in.

---

### Post by Amit_Oza on 2010-08-31
Dear ean5533,
 
Thank you very much for the response.

---

