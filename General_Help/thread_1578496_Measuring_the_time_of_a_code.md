---
title: "Measuring the time of a code"
date: 2010-09-20
forum: General Help
---

### Post by gaurish108 on 2010-09-20
I am a beginner to C and C++ and so far I have learned two ways to measure the time my program takes to run.

[COLOR=Red]Method 1[/COLOR]: Just compile your C file and if the executable is say a.out just type **time ./a.out**

[COLOR=Red]Method 2[/COLOR]: Here the general structure of the code is 
```
#include<stdio.h>
#include<time.h>

int main(void)

{
clock_t start, stop;

start= clock();
//Do whatever you want to do
stop=clock();

printf("Time taken is %f milliseconds", ((double) (stop-start)) / CLOCKS_PER_SEC);
}


```My questions are: 

[COLOR=Green]Question 1[/COLOR] Do Method 1 and Method 2 return the same times?

[COLOR=Green]Question 2[/COLOR] Method 1 gives three times ***real, usr*** and ***sys  ***. Is it true that USR+SYS= TIME GIVEN BY METHOD 2

I have performed some experiments with small codes which return the squares of numbers uptill 36000 and  I **feel **the answer to question 2 is yes

Since I am a beginner a detailed answer will be most appreciated. Thank you very much!!

---

### Post by afrowildo on 2010-09-20
This thread would probably be better off in the Programming section of the forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39). The programmers may miss your question if it's not placed in the right section.

If you're a beginner programmer, then this site is probably worth a look: [http://stackoverflow.com/](http://stackoverflow.com/). I'm also a beginner programmer and it's really helped me out. You get an answer to many C++ questions in minutes.

FWIW, I'm also interested in this answer.

---

### Post by papibe on 2010-09-20
> You can also get three times if you do this:
```
$ time -p ./a.out
```

Regards.

sorry I read too fast. Please ignore my answer.

---

