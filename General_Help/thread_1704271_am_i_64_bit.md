---
title: "am i 64 bit?"
date: 2011-03-10
forum: General Help
---

### Post by Spyderkid on 2011-03-10
Is there a command I can run to find out if my computer has 64bit capabilities?

---

### Post by Bcrowes11 on 2011-03-10
This link will tell you [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by amauk on 2011-03-10
```
cat /proc/cpuinfo
```

If you have "lm" (long mode) in the flags section, then your CPU is 64bit

---

### Post by TBABill on 2011-03-10
EDIT: Misread the OP's question

---

### Post by Grenage on 2011-03-10
> **Spyderkid said:**
> Is there a command I can run to find out if my computer has 64bit capabilities?

Alternatively:

```
uname -a
```

If you're x64, you'll see something like:
[I]
Linux ubqd 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 **x86_64** GNU/Linux[/I]

---

### Post by amauk on 2011-03-10
> **Grenage said:**
> Alternatively:

```
uname -a
```

If you're x64, you'll see something like:
[I]
Linux ubqd 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 **x86_64** GNU/Linux[/I]

this will only show your kernel architecture

If you're running 32bit OS on 64bit capable hardware, then it'll just return i686 (32bit)

---

### Post by Grenage on 2011-03-10
Ah, bonne;  I misread the post!

---

### Post by Spyderkid on 2011-03-11
I ran this command "grep --color=always -iw lm /proc/cpuinfo"

i got 4 lines which had a red lm at the front.

if i can use 64bit can i upgrade by running a command or do i just have to re-install?

---

### Post by plucky on 2011-03-11
> **Spyderkid said:**
> I ran this command "grep --color=always -iw lm /proc/cpuinfo"

i got 4 lines which had a red lm at the front.

if i can use 64bit can i upgrade by running a command or do i just have to re-install?

You have to re-install

---

### Post by Spyderkid on 2011-03-12
I won't bother then untill 11.04... does 64bit have any problems in general and is it noticibly faster or worth doing?

---

### Post by Spyderkid on 2011-03-12
So my new question is...

Is 64bit Ubuntu better than 32bit Ubuntu (Maverick Meerkat)
>By this I mean, Is it noticably faster?
>Are there as many applications on 64 compared to 32?
>Are there many Bugs?
>are there many advantages, disadvantages?

---

### Post by Spyderkid on 2011-03-12
[edit] double post sorry.

---

### Post by oldos2er on 2011-03-12
There are a few apps that are still 32-bit only, Adobe Acrobat, skype, and I forget what else. Also, there is a 64-bit version of flash but it is not yet in the repositories.

There aren't any bugs solely related to bitness that I'm aware of.

You might want to read [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)
It's a few years old, but still relevant in my opinion.

---

### Post by Bcrowes11 on 2011-03-12
64 bit doesn't have widespread support yet like 32 bit does. 64 bit and 32 bit are relatively new divides.also some updates won't install. But only for like third part apps. and actually skype DOES work for 64bit. I'm running it on myt 64bit.

---

### Post by oldos2er on 2011-03-12
I didn't say Skype didn't work, but that it has no 64-bit version.

---

### Post by Cracklepop on 2011-03-13
I know it's not technically a 64 bit version of skype, but skype does have a specific download for 64 bit Ubuntu, wich installs and runs exactly as the 32 bit version does on 32 bit Ubuntu.

It would of course be preferable for skype to pull their fimgers out and do an actual 64 bit version, but the point is skype is not an issue that even needs to cross the mind of someone installing 64 bit Ubuntu for the first time.

---

### Post by Spyderkid on 2011-03-13
So is it noticeably faster?

---

### Post by Dutch70 on 2011-03-13
LOL, this is the great debate. Some say it is, Some say not really. Also, it depends on your RAM for starters. If you want to take advantage of more than 3.6GB (roughly) of your RAM. Then you'll have to install the 64bit version. If you have little RAM, there is even a greater debate. Although there are several people on this board that run the 64bit version with as little as 512MB of RAM, and love it. I have 4GB RAM and 64-bit feels faster & I'm glad I reinstalled.

If you're cpu has 64-bit capabilities, I'd take advantage of it.
The link given to you by oldos2er, is a really good read.

---

### Post by Spyderkid on 2011-03-13
I have 4GB RAM and a Quad-Core processor

---

### Post by Vaphell on 2011-03-13
go with 64bit and separate /home partition. If you meet any 64bit specific roadblocks you can always wipe the system partition, reistall in 32bit flavor and all your settings and personal files are picked up by the system right off the bat (just select /home to be /home during installation and obviously don't format it). Separate /home makes reinstallation a 15min long breeze and user space doesn't care about the 'bitness' of the system :)

---

### Post by oldos2er on 2011-03-13
> **Spyderkid said:**
> So is it noticeably faster?

Tasks like video encoding are noticeably faster. Things like web browsing, email, etc., not so much.

---

### Post by Spyderkid on 2011-03-13
ok also 1 thing is.... does anyone know if gnomenu works on 64bit because I really quite like it.

---

### Post by oldos2er on 2011-03-13
Yes.

---

### Post by Cracklepop on 2011-03-14
> **Dutch70 said:**
>  The link given to you by oldos2er, is a really good read.

Not without a few points to pick on though, and very old (and the links there are even okder). 

See this: >  2) The other question an user might ask is does more bits mean better performance? Depending on whom you ask maybe / maybe not. What you will see is a performance increase for applications that use 64-bit integers, however. This is where a con comes into play. The con being (Do not expect most of your applications to run any faster than they do on your 32-bit systems.) Examples: your web browser will still be limited by your Internet connection speed, and your word processing program speed will still be tied to how fast you can type, etc. Some users feel there can also be a slight performance decrease caused by switching to a 64-bit processor, due to the larger memory address pointers taking up twice as much room in the cache.  A performace increase for apps that use 64 bit ints? Yes, but that's not the only performance incresae... 

Also true that it's theoretically possible for the larger pointers to cause a decrease inperformance, but this is extremely unlikely, and also a very strong indication that you should run out and buy some more ram, even if you stay with a 32 bit OS.

You can take this as a general truth in this discussion: performance will increase, but you probably won't notice it.  If you have 64 bit hardware, use 64 bit software.

---

