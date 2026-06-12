---
title: "Having Problems with Ubuntu 10.04"
date: 2010-07-05
forum: General Help
---

### Post by Honey_HR on 2010-07-05
I am very new to Ubuntu and having some problems with it.
My graphics are not good, I mean it take some time to open up a window or any software, and While playing video files, its not good its looks like i mean, not playing well,some times it shows video but some times black then after some time shows video,and some times system hangs very badly or shows Whole black screen, then i ve to restart, coz there is no any other option:(
I am on

Celeron 1.7 MGH
DDR 1GB
Motherboard- Gigabyte 8I845GVMRZ

PLEASE GUYS HELP ME BRO.

---

### Post by Rubi1200 on 2010-07-05
If you are having graphics problems, we need to know what type of graphics card you have installed.

Go to Applications > Accessories > Terminal

Use this code:

```
lspci -nn | grep VGA
```

Then post the results back here.

---

### Post by Honey_HR on 2010-07-05
> **Rubi1200 said:**
> If you are having graphics problems, we need to know what type of graphics card you have installed.

Go to Applications > Accessories > Terminal

Use this code:

```
lspci -nn | grep VGA
```

Then post the results back here.

Thanks for reply man here it is :

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

---

### Post by lukeiamyourfather on 2010-07-05
The hardware is probably too slow to play videos with modern codecs like H.264 which is what Youtube and a lot of other sites use. So it might not be Ubuntu, but the hardware itself.

---

### Post by Honey_HR on 2010-07-05
> **lukeiamyourfather said:**
> The hardware is probably too slow to play videos with modern codecs like H.264 which is what Youtube and a lot of other sites use. So it might not be Ubuntu, but the hardware itself.

So is There any way to fix it, or ubuntu 9.10 is good for me ??? can you tell me please which version is best for me ?? i mean 10.04, ubuntu 9.10 or any other old version ???

---

### Post by lukeiamyourfather on 2010-07-05
> **Honey_HR said:**
> So is There any way to fix it, or ubuntu 9.10 is good for me ??? can you tell me please which version is best for me ?? i mean 10.04, ubuntu 9.10 or any other old version ???

I would try Xubuntu 10.04 ([http://www.xubuntu.org/news/10.04-release](http://www.xubuntu.org/news/10.04-release)) since it uses the less resource heavy Xfce for the interface. Chances are though the system is too old to do much with besides basic browsing (not video), email, word processing, other basics. Since the hardware is circa 2002 its not a big surprise that it seems slow. Might be time to start looking for upgrades or a new system if you want to do more with the system besides those basic tasks. Cheers!

---

### Post by Rubi1200 on 2010-07-05
> **Honey_HR said:**
> So is There any way to fix it, or ubuntu 9.10 is good for me ??? can you tell me please which version is best for me ?? i mean 10.04, ubuntu 9.10 or any other old version ???

When did you install Lucid 10.04?

Have you tried running 9.10 as a LiveCD?

There may be a fix for this but it depends a little bit on **when** you installed Lucid.

I assume you can boot normally right?

Personally, I have stayed with 9.10 because it is supported until next April and I have never had any issues with it.

On my test system, I have had many of the issues that we are now seeing on the forums with 10.04.

My advice: if you don't need the latest and greatest, stick with 9.10 until the major bugs are ironed out.

---

