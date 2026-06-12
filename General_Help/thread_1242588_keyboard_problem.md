---
title: "keyboard problem?"
date: 2009-08-17
forum: General Help
---

### Post by jARLAXL on 2009-08-17
Hello everybody,

I have a very starnge keyboard problem:
1. when i use ctrl-c it never interupts a process in gnome terminal but instead outputs the respective character of my greek locale (&#968;).
2. That is the main problem. when i start matlab (2007a), keyboard is frozen and cannot type anything under matlab. However, when i start matlab with 
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.14/jre
```
then only greek characters can be typed in command or editor window nomatter what localeis chosen.

It looks as the two problems are related. So far i havent found a solution. Any help is much appreciated.

Thanks,

Jarlaxl

Update: Keys that are not working undermatlab: a-z. All others work fine (i.e 0-9 ; , . > etc)

---

### Post by jARLAXL on 2009-08-17
bump](*,)

---

### Post by jARLAXL on 2009-08-18
Ok had to reinstall but got what the problem was:
the keyboard defined was mistakenly the greek and not the us.
Cheers

---

