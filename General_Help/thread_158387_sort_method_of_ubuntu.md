---
title: "sort method of ubuntu"
date: 2006-04-11
forum: General Help
---

### Post by martijn1981 on 2006-04-11
Hello,

could anyone tell me how I change the sort method that is used by linux commands, such as *ls*. The problem actually is that all linux commands / applications skip tokens such as *_* and *+*. I will explain the problem by giving an example. When we have two words, say _B and A, *ls* will deliver the following result:
A
_B

I want this command giving me back:
_B
A

I hope I made clear my problem and that someone knows a solution!

Thankz.
Martijn

---

### Post by cwaldbieser on 2006-04-12
[QUOTE=martijn1981]Hello,

could anyone tell me how I change the sort method that is used by linux commands, such as *ls*. The problem actually is that all linux commands / applications skip tokens such as *_* and *+*. I will explain the problem by giving an example. When we have two words, say _B and A, *ls* will deliver the following result:
A
_B

I want this command giving me back:
_B
A

I hope I made clear my problem and that someone knows a solution!

Thankz.
Martijn[/QUOTE]

This is a little tricky.  I find that the sort command sorts lowercase letters the way you want:
_b
a

You could just "tr" the uppercase characters to lowercase, but I don't know if you need to preserve the case.

---

### Post by IYY on 2006-04-12
> he problem actually is that all linux commands / applications skip tokens such as _ and +.

Nope, it doesn't skip them, it just considers them as coming after the alphanumeric characters. For example, I could get a directory listing like:

A
B
C
_B

So, really all you want to do is take the lines starting with _ and placing them at the beginning instead of end. You could do

ls -1 | grep ^_
ls -1 | grep -v ^_

and this will print all the files starting with _ first, and then all the files that don't. I don't know if it solves your particular problem, because I don't know exactly what you need it for.

---

