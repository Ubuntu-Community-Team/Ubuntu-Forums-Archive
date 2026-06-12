---
title: "is this my cpu problem?"
date: 2010-06-08
forum: General Help
---

### Post by pooya_mr2009 on 2010-06-08
hi every body
i have ubuntu 10.04 and dell laptop core 2 due and 2.6 MGhz
sometimes my c++ codes runs very slowly and when i see my result of 'top" command or
cpu info in the cpu panel i don't see that cpu is full even i see it's empty fully!
what is this problem and how can i fix it
thank's a lot
bye

---

### Post by cbecker78 on 2010-06-08
Can you post the output of "top -n 1" -run the command when you are experiencing the problem.

---

### Post by pooya_mr2009 on 2010-06-09
sorry
i can't run this command in that time because i'm not sure that when the speed will be reduce!
but usually that i use "top" ,the maximum of used percent was 6 for (xorg)
do you have another suggestion?
tnx a lot 
bye

---

### Post by cbecker78 on 2010-06-09
Well, one other thought:  If you are experiencing the issue, make sure too look at memory/swap also, as you could have a bug in your program that is leaking memory, and even though it is not taking up cpu, it is leaving your os with little room to breath.

^^that's the best I got right now.  to be honest, I don't quite understand the issue entirely, and was hoping looking at top during the problem would help me understand the issue and maybe give a clue towards how to solve it.

So, I guess instead, we could try some clarification (to help my rather slow mind):

1:  You said this happened during C++ codes... do you mean "when" you are doing the coding... when you are compiling, or just when you are running a program built in C++.

2: Does the slow down happen at other times?

3: Describe what exactly is slowing down...  mouse and screen response?  Just a compiler or single program, the whole computer?

4: Is the hard drive busy when it is having the problem? (you could tell by the blinking light)

---

### Post by john newbuntu on 2010-06-09
Since you mention "c++ codes runs very slowly", my guess is that this is an execution time problem.  I am assuming you have adequate memory/swap on your box. I would suggest using a profiler such as gprof or valgrind to check for possible memory leaks and unnecessary time spent for either I/O or cpu in certain functions.

---

### Post by pooya_mr2009 on 2010-06-09
> **cbecker78 said:**
> Well, one other thought:  If you are experiencing the issue, make sure too look at memory/swap also, as you could have a bug in your program that is leaking memory, and even though it is not taking up cpu, it is leaving your os with little room to breath.

^^that's the best I got right now.  to be honest, I don't quite understand the issue entirely, and was hoping looking at top during the problem would help me understand the issue and maybe give a clue towards how to solve it.

So, I guess instead, we could try some clarification (to help my rather slow mind):

1:  You said this happened during C++ codes... do you mean "when" you are doing the coding... when you are compiling, or just when you are running a program built in C++.

2: Does the slow down happen at other times?

3: Describe what exactly is slowing down...  mouse and screen response?  Just a compiler or single program, the whole computer?

4: Is the hard drive busy when it is having the problem? (you could tell by the blinking light)


tnx
my answers:
1-i have problem at running code
2-no
3-program running is slowing down
4-no
what is best work for me for fix this problem?
tnx

---

### Post by lavinog on 2010-06-09
can you post the code?

---

### Post by cbecker78 on 2010-06-09
> **pooya_mr2009 said:**
> tnx
what is best work for me for fix this problem?
tnx

Based on your answers, the best way to troubleshoot is probably going to be debugging your code.  I won't be of much use there.

---

### Post by Captain Giraffe on 2010-06-09
Im guessing you have a cpu core problem or a cpu clock() problem. Om linux clock() measures cpu time wasted on your program. cin<< wont take much time... otoh if you are comparing to a MS c++ sort() they have multithreaded versions of the entire c++ library. Why dont we?

---

### Post by pooya_mr2009 on 2010-06-10
> **Captain Giraffe said:**
> Im guessing you have a cpu core problem or a cpu clock() problem. Om linux clock() measures cpu time wasted on your program. cin<< wont take much time... otoh if you are comparing to a MS c++ sort() they have multithreaded versions of the entire c++ library. Why dont we?

so for fix this problem(cout << or cin >>) what should i do?
tnx a lot

---

