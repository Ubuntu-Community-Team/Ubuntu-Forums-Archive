---
title: "POSIX threads"
date: 2010-05-17
forum: General Help
---

### Post by youralibaba on 2010-05-17
In c++ POSIX  thread programming.
 
#include<pthread.h>
void *function(void *parameter);

void main(){
int input;
pthread_create(thread ID, NULL, function, (void *) input);

}

The question is why there is (void *) input in the argument of  pthread_create ? Shouldn't the argument be &input ? The function is  void *function(void *). It should be given &input in the argument.  Why is input casted to void * ?

---

