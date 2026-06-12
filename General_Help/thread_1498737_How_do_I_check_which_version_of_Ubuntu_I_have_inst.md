---
title: "How do I check which version of Ubuntu I have installed on my computer"
date: 2010-06-01
forum: General Help
---

### Post by glynn on 2010-06-01
This has probably been answered elsewhere, but I could not see it - how can I check which version of Ubunbtu I have installed and whether it is 32 or 64 bit?

---

### Post by howefield on 2010-06-01
Open a terminal (Applications > Accessories > Terminal) and tpye

```
uname -a
```

if it has _64 somewhere in the output, you have 64 bit, otherwise it is 32 bit.

Or look at the menu option in Firefox, Help > About Mozilla Firefox.

---

### Post by Jakiejake on 2010-06-01
> **glynn said:**
> This has probably been answered elsewhere, but I could not see it - how can I check which version of Ubunbtu I have installed and whether it is 32 or 64 bit?

System -> About Ubuntu

---

### Post by glynn on 2010-06-01
Thanks.  

glynn@glynn-desktop:~$ uname -a
Linux glynn-desktop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux
glynn@glynn-desktop:~$ 

This would mean that I am running a 32 bit version?

---

### Post by Jakiejake on 2010-06-01
> **howefield said:**
> Open a terminal (Applications > Accessories > Terminal) and tpye

```
uname -a
```

if it has _64 somewhere in the output, you have 64 bit, otherwise it is 32 bit.

Or look at the menu option in Firefox, Help > About Mozilla Firefox.

Or What He Said

---

### Post by glynn on 2010-06-01
> **Jakiejake said:**
> System -> About Ubuntu

Thanks - this shows that I am using  Ubuntu 9.04 - the Jaunty Jackalope - released in April 2009.

32 or 64 bit information?

---

### Post by arjunak01 on 2010-06-01
open a terminal and type
```
uname -m
```
if the output is "x86_64" then it is 64 bit

---

### Post by Jakiejake on 2010-06-01
> **glynn said:**
> Thanks.  

glynn@glynn-desktop:~$ uname -a
Linux glynn-desktop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux
glynn@glynn-desktop:~$ 

This would mean that I am running a 32 bit version?

I run Ubuntu 10.04 Lucid Lynx 64 Bit
This is what I get
> jacob@jacob-desktop:~$ uname -a
Linux jacob-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
jacob@jacob-desktop:~$ 




---

### Post by arjunak01 on 2010-06-01
you are running 32 bit

---

### Post by Jakiejake on 2010-06-01
> **arjunak01 said:**
> open a terminal and type
```
uname -m
```
if the output is "x86_64" then it is 64 bit

A bit late there :popcorn:

---

### Post by glynn on 2010-06-01
So - it seems that your excellent help has shown me that I am using 9.04, 32 bit version.  Since my chip is an AMD 3200+, I suspect that it should be able to use the 64 bit version - is there any benefit over the 32 bit one?

---

### Post by Jakiejake on 2010-06-01
> **glynn said:**
> So - it seems that your excellent help has shown me that I am using 9.04, 32 bit version.  Since my chip is an AMD 3200+, I suspect that it should be able to use the 64 bit version - is there any benefit over the 32 bit one?

Speed
I had 32 bit 10.04 but switched to the 64 bit version because 64 bit is the future

---

### Post by Jakiejake on 2010-06-01
> **glynn said:**
> So - it seems that your excellent help has shown me that I am using 9.04, 32 bit version.  Since my chip is an AMD 3200+, I suspect that it should be able to use the 64 bit version - is there any benefit over the 32 bit one?

How much RAM have you got?

---

### Post by glynn on 2010-06-01
1G of RAM - running XP SP3 and Ubuntu

---

### Post by howefield on 2010-06-01
> **glynn said:**
> is there any benefit over the 32 bit one?

Here's an interesting link for you.

[http://www.tuxradar.com/content/ubun...bit-benchmarks](http://www.tuxradar.com/content/ubun...bit-benchmarks)


Edit :
Also if you want to make sure that your cpu is indeed 64 bit capable, type the following in a terminal

```
cat /proc/cpuinfo
```

If you see lm in the list of flags, your cpu is 64 bit capable.

---

### Post by Jakiejake on 2010-06-01
> **glynn said:**
> 1G of RAM - running XP SP3 and Ubuntu

Not worth it
You would only notice a difference between 32 and 64 if you had 4GB of ram or more

---

### Post by howefield on 2010-06-01
> **Jakiejake said:**
> You would only notice a difference between 32 and 64 if you had 4GB of ram or more

Rubbish.

Pure rubbish ;-)

---

### Post by Jakiejake on 2010-06-02
> **howefield said:**
> Rubbish.

Pure rubbish ;-)

Oh really now?

---

### Post by Jakiejake on 2010-06-02
> **howefield said:**
> Rubbish.

Pure rubbish ;-)

Ok then
It would make a bit of a difference...
But the more RAM you got the better 64 bit will be! ;)

---

### Post by Jakiejake on 2010-06-02
> **glynn said:**
> So - it seems that your excellent help has shown me that I am using 9.04, 32 bit version.  Since my chip is an AMD 3200+, I suspect that it should be able to use the 64 bit version - is there any benefit over the 32 bit one?

Is this your processor?
[http://www.pcstats.com/articleview.cfm?articleID=1469]("http://www.pcstats.com/articleview.cfm?articleID=1469")
If it is it can run 64 Bit!

---

### Post by howefield on 2010-06-02
> **Jakiejake said:**
> Ok then
It would make a bit of a difference...
But the more RAM you got the better 64 bit will be! ;)

A bright spot on an otherwise dull day, to see someone continue an education. Continue reading though, there is more to 64 bit than the RAM total.

I do hope this post doesn't spawn another plethora of replies ;)

---

