---
title: "Lag for no reason"
date: 2010-07-15
forum: General Help
---

### Post by rt-2 on 2010-07-15
Hi,
Recently, I've got my new laptop, a ASUS n70.
This is a pretty fast computer compared to what linux needs to work properly.
BUT, every like, 2 minutes, my mouse lag, some program lags or just linux itself.
When this happens, I'm just using it like it should be, and not running some high needs applications. It just happens like that.

I've tried to tell the CPUs to run at there maximum speed all the time, but it didn't worked.

I also seen this while i was writting this message.
[IMG]http://i574.photobucket.com/albums/ss187/rt-2/Screenshot.png[/IMG]
and during that time... only one process was using CPU's and it was at 6%... but this is the first time i see this.


Please help.

Thank you

---

### Post by nemilar on 2010-07-16
Since this seems to happen often, can you open a terminal and run

```
top
```

When you have the problem, take a screenshot and post it here.  It will show what process is pegging the CPU to 100%.

---

### Post by rt-2 on 2010-07-16
Thanks form the reply, but... my problem is that it just jam for 10-20 sec, so that my mouse don't even respond some time, or it's the only thing that response... so i wouldn't be able to find wich process is causing all this... 

Plus, the screenshot is a problem that happent only once... and i never seen it after, the real problem really is the computer jamming for 10-20 secs. and i'm not able to do anything. and 10 sec after it unjam, like if nothing happent

Thanks for your help, and sorry for my spelling, i'm french but trying :D

---

### Post by rt-2 on 2010-07-16
I foudn what was the process that do all this stuff... i'S Xorg, i played tetris with "top" opened bytside, and when it jammed, i looked carefully to the top,,, when unjamming, we can see Xorg at 99-100%

I'm going to make further researches about that

---

### Post by rt-2 on 2010-07-17
Guys, I've discovered that my problem is the Xorg problem, involving nvidia

My video card is an Nvidia GeForce GT 130M 1GB (this is a laptop)
My driver version is 256.35 (downloaded from nvidia's website)
The one from ubuntu itself did the same thing...

I've done searchs and it doesn't seems to have any solution at that time... I don't mind about a lose of graphic force, if it's to be stable it's better...

Thanks for further help

---

