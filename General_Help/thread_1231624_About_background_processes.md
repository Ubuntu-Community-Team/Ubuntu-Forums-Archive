---
title: "About background processes"
date: 2009-08-04
forum: General Help
---

### Post by ooobooontooo on 2009-08-04
Hi,

I was wondering, are background processes given less priority/cpu time/niceness level/whatever? By background processes, I mean processes that are run with an & in the command line. ("./a.out &" as opposed to just "./a.out")

---

### Post by finch127 on 2009-08-04
not to my knowledge, i did a quick glxgears & and used top, and the nice value was 0 / neutral. so it seems the answer is no

---

### Post by lisati on 2009-08-04
Have a look here: [http://en.wikipedia.org/wiki/Background_process](http://en.wikipedia.org/wiki/Background_process)

You might want to think of a background process as something that is useful (or just nice) to have running on your system, but that you don't want to have hogging resources in a way that prevents you from doing useful work on your computer.

---

### Post by ooobooontooo on 2009-08-04
@finch127
Haha.... I guess that would've been the obvious solution. Thanks.

@lisati
I'm sorry. I guess I wasn't clear enough. By background processes, I simply meant processes that are not run in the foreground. That is, processes that are run with an & in the command line. I was wondering whether this type of background processes affected the scheduler in any way.

EDIT: fixed grammatical errors

---

### Post by lisati on 2009-08-04
> **ooobooontooo said:**
> 
@lisati
I'm sorry. I guess I wasn't clear enough. By background processes, I simply meant processes that are not run in the foreground. That is, processes that are run with an & in the command line. I was wondering whether this type of background processes affected the scheduler in any way.

That's what I was referring to as well. :)

---

### Post by ooobooontooo on 2009-08-04
> **lisati said:**
> That's what I was referring to as well. :)

Really?...:confused: ....I did take a look at the wiki link and it said that background processes are processes who are given low priority. But, that's a direct contrast of finch127's findings....about the niceness levels and all that...

---

### Post by finch127 on 2009-08-04
Yeah: 0 is not high but it isn't low, it said relatively low so I would suppose that concurs with my findings. Remember that 0 is arbitrary.

---

### Post by ooobooontooo on 2009-08-04
Yes, but from my experiment, there isn't a change in the nice level between running "./a.out" and "./a.out &", so I don't quite understand what it means by the priority being relatively low...

---

### Post by finch127 on 2009-08-04
well -20 is very fast, 20 is very low, so 0 is in the middle yes? which if you run "top" you will see that most of the background processes are at -5 meaning that they are faster. To calculate CPU time for each, it is 20-(nice value) divided by 20, so for example, a +5 would be 20-5 which is 15, and 15/20 equals 3/4. So therefore, a program with nice 5 gets 3/4 the normal cpu time.

EDIT, I just got what you meant, I am an idiot sometimes. Yes it means that most of the time, they are run with relatively low nice IDs but that doesnt happen on Linux, I suppose its a windows carryover or something. As you can see its not the case.

---

### Post by ooobooontooo on 2009-08-05
> **finch127 said:**
> well -20 is very fast, 20 is very low, so 0 is in the middle yes? which if you run "top" you will see that most of the background processes are at -5 meaning that they are faster. To calculate CPU time for each, it is 20-(nice value) divided by 20, so for example, a +5 would be 20-5 which is 15, and 15/20 equals 3/4. So therefore, a program with nice 5 gets 3/4 the normal cpu time.

EDIT, I just got what you meant, I am an idiot sometimes. Yes it means that most of the time, they are run with relatively low nice IDs but that doesnt happen on Linux, I suppose its a windows carryover or something. As you can see its not the case.

I agree with everything you said except I always thought nice levels were been -20 and 19 inclusive....small detail. Also, I believe the scheduler assigns slightly different weights for processes than the direct proportion of the nice levels (so a +5 would probably get less than 3/4 the cpu time)...at least from my understanding. Anyway, I guess I should go test it out on a BSD/Solaris box. Thanks for your help.

---

### Post by 3rdalbum on 2009-08-05
In the Linux kernel, nothing is a "background process".

However, the way the scheduler works, if a program has been using lots of CPU cycles for a while and suddenly another program wants to use the CPU, the second program will get priority. So if you define a "background process" as "one that has been doing work while I do other things", then your "other things" will take priority, unless they have been using heavy CPU time longer than your background process.

---

### Post by ooobooontooo on 2009-08-05
> **3rdalbum said:**
> In the Linux kernel, nothing is a "background process".

However, the way the scheduler works, if a program has been using lots of CPU cycles for a while and suddenly another program wants to use the CPU, the second program will get priority. So if you define a "background process" as "one that has been doing work while I do other things", then your "other things" will take priority, unless they have been using heavy CPU time longer than your background process.

Makes sense. Thanks for your help.

---

