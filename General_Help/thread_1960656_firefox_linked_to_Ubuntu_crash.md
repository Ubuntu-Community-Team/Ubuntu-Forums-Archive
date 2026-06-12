---
title: "firefox linked to Ubuntu crash"
date: 2012-04-17
forum: General Help
---

### Post by iebng on 2012-04-17
Hi,
I use ver 11.04 Natty Narwhal, recently I was browsing the net using Firefox browsers, I used this Downthem all add on to download clips from youtube.

Of late the firefox use to crash, this time i check the details and it pointed to the firefox add on.

I removed add on.

Suddenly i got this black screen with some text. 

I decided to restart again but I cannot get the OS running.

I tried the recovery counsel, it start executing some text but it stop.

Luckly i had Windows XP along with Ubuntu so I was able to work, even there i experience some error message while running applications.

What could be the problem.

How to solve this problem.

Thanks

---

### Post by oboedad55 on 2012-04-17
> **iebng said:**
> Hi,
I use ver 11.04 Natty Narwhal, recently I was browsing the net using Firefox browsers, I used this Downthem all add on to download clips from youtube.

Of late the firefox use to crash, this time i check the details and it pointed to the firefox add on.

I removed add on.

Suddenly i got this black screen with some text. 

I decided to restart again but I cannot get the OS running.

I tried the recovery counsel, it start executing some text but it stop.

Luckly i had Windows XP along with Ubuntu so I was able to work, even there i experience some error message while running applications.

What could be the problem.

How to solve this problem.

Thanks

We need any error messages you can supply. I can't see how Firefox or its addons can trash a system. What else were you doing at the time? Is this a dual-boot setup? The fact that you're now having trouble with Windows points to it not being an Ubuntu problem. Again, we need any error messages you can provide.

---

### Post by cheat117 on 2012-04-18
what is your native language? no offense but some of this is broken english.

We'd be glad to help if you could tell us your language first or the type of error. Until then I suggest using a LiveCD and finding your firefox directory and copying the files from the LiveCD to that directory! good luck!

---

### Post by iebng on 2012-04-18
I have taken these photos.

[https://docs.google.com/open?id=0B34ztznuQwM6enR5RDdOWFhFVEE](https://docs.google.com/open?id=0B34ztznuQwM6enR5RDdOWFhFVEE)
[https://docs.google.com/open?id=0B34ztznuQwM6RVB0aXh4c0V4M0k](https://docs.google.com/open?id=0B34ztznuQwM6RVB0aXh4c0V4M0k)
[https://docs.google.com/open?id=0B34ztznuQwM6MldmTWxDSEJyMzA](https://docs.google.com/open?id=0B34ztznuQwM6MldmTWxDSEJyMzA)
[https://docs.google.com/open?id=0B34ztznuQwM6NzQ5OWU1enIyVGc](https://docs.google.com/open?id=0B34ztznuQwM6NzQ5OWU1enIyVGc)
[https://docs.google.com/open?id=0B34ztznuQwM6Mm5FVExqUUV3ZUU](https://docs.google.com/open?id=0B34ztznuQwM6Mm5FVExqUUV3ZUU)

It goes like this

I get this BIOS screen and later a screen appear with option to choose the OS. 
when i choose Ubuntu
I get a blank screen with cursor blinking and nothing happens.

I restart the system and this time i choose Ubuntu (recovery)
and i get this black screen with text and nothing happens.

One thing i noticed that earlier i could the choosing screen with time option in the bottom of screen (like in seconds), now i don't.

Can something be done to correct it.

Thanks

---

### Post by Bucky Ball on 2012-04-18
If you're having problems in Ubuntu and Windows this would point to a hardware issue rather than software ...

---

### Post by oboedad55 on 2012-04-18
> **iebng said:**
> I have taken these photos.

[https://docs.google.com/open?id=0B34ztznuQwM6enR5RDdOWFhFVEE](https://docs.google.com/open?id=0B34ztznuQwM6enR5RDdOWFhFVEE)
[https://docs.google.com/open?id=0B34ztznuQwM6RVB0aXh4c0V4M0k](https://docs.google.com/open?id=0B34ztznuQwM6RVB0aXh4c0V4M0k)
[https://docs.google.com/open?id=0B34ztznuQwM6MldmTWxDSEJyMzA](https://docs.google.com/open?id=0B34ztznuQwM6MldmTWxDSEJyMzA)
[https://docs.google.com/open?id=0B34ztznuQwM6NzQ5OWU1enIyVGc](https://docs.google.com/open?id=0B34ztznuQwM6NzQ5OWU1enIyVGc)
[https://docs.google.com/open?id=0B34ztznuQwM6Mm5FVExqUUV3ZUU](https://docs.google.com/open?id=0B34ztznuQwM6Mm5FVExqUUV3ZUU)

It goes like this

I get this BIOS screen and later a screen appear with option to choose the OS. 
when i choose Ubuntu
I get a blank screen with cursor blinking and nothing happens.

I restart the system and this time i choose Ubuntu (recovery)
and i get this black screen with text and nothing happens.

One thing i noticed that earlier i could the choosing screen with time option in the bottom of screen (like in seconds), now i don't.

Can something be done to correct it.

Thanks

OK, question. Did you set /home as a separate partition? In any case, if it were my system I would make sure that I have anything I want to save backed up. It would help if you would also describe your Windows problems as they may be connected, i.e. it may be a hardware problem, which is what I suspected earlier. I'm not a big fan of reinstalling the operating system, I prefer to solve the problems. However,in this case it may best to do just that. If you have /home on its own partition you won't lose your data.:neutral:

---

### Post by iebng on 2012-04-18
Thanks,

I have seperate partition for Ubuntu.

also, i ran the memory test.

It shown

error: too small lower memory ( 0x99100 > 0x8f000).

Is the problem around GRUB or corrupted app in ubunut.

This starting happening after firfox crashed several times and detials of the file (crash file) points to an 'Add on' in firefox, i removed the 'add on' and the computer cannot boot into Ubuntu.


Is is better to reinstall unbuntu. I'm not experience any problems working with Windows XP.

It easily boots into Windows XP (having choosen the option)

Thanks

---

### Post by oboedad55 on 2012-04-18
> **iebng said:**
> Thanks,

I have seperate partition for Ubuntu.

also, i ran the memory test.

It shown

error: too small lower memory ( 0x99100 > 0x8f000).

Is the problem around GRUB or corrupted app in ubunut.

This starting happening after firfox crashed several times and detials of the file (crash file) points to an 'Add on' in firefox, i removed the 'add on' and the computer cannot boot into Ubuntu.


Is is better to reinstall unbuntu. I'm not experience any problems working with Windows XP.

It easily boots into Windows XP (having choosen the option)

Thanks

In your first post you mentioned having problems with Windows too. If that's not the case I would just reinstall Ubuntu, perhaps this time making two partitions, one for /root and one for /home, in addition to /swap of course. :neutral:

---

### Post by iebng on 2012-04-18
but, I have two separate partitions.

You meant to say that, its better to reinstall the unbuntu to solve this problem.

I'm not familiar with Linux part (that's why I'm in this forum)

Can you provide me an links to reinstall the unbuntu or the issue can be solved ?

What about the memory test error, any solution for it.

Thanks

---

### Post by oboedad55 on 2012-04-18
> **iebng said:**
> but, I have two separate partitions.

You meant to say that, its better to reinstall the unbuntu to solve this problem.

I'm not familiar with Linux part (that's why I'm in this forum)

Can you provide me an links to reinstall the unbuntu or the issue can be solved ?

What about the memory test error, any solution for it.

Thanks

No clue about that memory thing since I have no way of knowing what test you ran. All of the information you seek about partitioning, reinstalling, and everything else is readily accessible via Google or another search engine.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

