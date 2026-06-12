---
title: "Java has high %CPU"
date: 2010-11-01
forum: General Help
---

### Post by birdkathe on 2010-11-01
Hi,

I'm running Ubuntu 9.10 (I know I'll upgrade this winter). I've started to notice that java is eating way more CPU time then it has any right to, even with a fresh reboot and Firefox closed. I have java version: 
> java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.2) (6b18-1.8.2-4ubuntu1~9.10.1)
OpenJDK 64-Bit Server VM (build 16.0-b13, mixed mode)


Here is a snip of my top screen. Keep in mind that I just restarted ~30 minutes prior. I find the claim of 9+hours of runtime by the java process alarming as well as the %CPU which will vary between %15-%80 or so.

> 
top - 08:36:54 up 25 min,  4 users,  load average: 0.12, 0.32, 0.43
Tasks: 175 total,   2 running, 173 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.1%us, 11.2%sy, 19.0%ni, 48.8%id, 13.1%wa,  0.3%hi,  0.5%si,  0.0%st
Mem:   8193692k total,  1499072k used,  6694620k free,   119292k buffers
Swap:  7815612k total,        0k used,  7815612k free,   518416k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1710 root      39  19 1007m 185m  19m S   57  2.3   9:35.87 java               
 3541 kathe     20   0  298m  17m  12m S    9  0.2   0:00.26 gedit


Thoughts? I'm not even sure how to go about debugging this.

-Kathe

---

### Post by maxsideburn on 2010-11-01
simple. Java sucks, always has always will.

---

### Post by birdkathe on 2010-11-01
Issue solved. CrashPlan was stuck in a loop trying to back up to a full remote directory. This was showing up as a 'java' process for some reason. Would still love to know how to track processes back to their parents in top if anyone could enlighten me. 

@maxsideburn Not useful. Java may suck but the workarounds entailed in not using it suck more.

---

