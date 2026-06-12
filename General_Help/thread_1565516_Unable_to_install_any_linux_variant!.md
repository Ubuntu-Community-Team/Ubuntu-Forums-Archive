---
title: "Unable to install any linux variant!"
date: 2010-09-01
forum: General Help
---

### Post by branko.savic on 2010-09-01
I just got a new laptop (Dell Inspiron M501-4049) With preinstalled W7, now I want to unstall ubuntu 10.04.1 but half way into loading live cd it gets a distorted picture and freezes!

Same thing happends with fedora 13, it starts loading the live cd but half way trough it just freezes!

Reinstalling Windows 7 works without any problem!
Could this laptop be locket someway so that only windows will work, or can I somehow force it to install ubuntu or fedora?

Thanks in advance!

---

### Post by utnubuuser on 2010-09-01
Check your BIOS has Plug-and-Play operating-system enabled.
And you might also want to try an older version, ie: 8.04, which doesn't use kernel-modesetting the way Lucid and the other newer distros do.

---

### Post by Elaztic on 2010-09-01
Have you tried to run the 'check disc for errors' before running the installation itself?
On ubuntu it is in the same menu where you can either choose to install or use as live-cd.

---

### Post by branko.savic on 2010-09-01
Ok, so here is what I have tried so far!

1. In BIOS there is no Plug n play OS option!
2. I am using my USB stick to boot, I have checked for errors (In the live cd menu option) and no errors where found!
3. I tried to burn ubuntu 10.04.1 on a cd
4. I tried ubuntu 8.04

Nothing helps! :-(

Any more suggestions would be greatly appreciated!

---

### Post by mike555 on 2010-09-01
What graphics do you have ?

---

### Post by branko.savic on 2010-09-01
> **mike555 said:**
> What graphics do you have ?

ATI Mobility Radeon HD 4250

---

### Post by branko.savic on 2010-09-01
Anyone?

---

### Post by mike555 on 2010-09-01
I'm thinking ATi is the problem , have you tried starting with different settings ? by clicking f6

---

### Post by Ocxic on 2010-09-01
Try the alternate CD

---

### Post by wojox on 2010-09-01
> **mike555 said:**
> I'm thinking ATi is the problem , have you tried starting with different settings ? by clicking f6

+1 that's a good suggestion. 

You mean you can't even get to the live desktop right? Not half way through the actual install.

---

### Post by branko.savic on 2010-09-01
> **wojox said:**
> +1 that's a good suggestion. 

You mean you can't even get to the live desktop right? Not half way through the actual install.

Correct, I am not even getting in to the live desktop!
Will try the alternate cd and report back, this is getting very frustrating!

Cant imagine that I am the only one with this problem!

The most interesting thing is that it wont even boot up with fedora 13, it just freezes half way into booting the live desktop! (The bootup screen looks good in fedora tough, not distorted like in ubuntu!)

---

### Post by mike555 on 2010-09-01
You might try a verbose mode by clicking f1 (I think) during boot ,then read it as it goes, I'll bet it's stopping on video ..

.. now that I think about it , I think it's ALT + F1

---

### Post by gypsumwolf on 2010-09-01
> **Ocxic said:**
> Try the alternate CD

+1

Found this useful on a laptop.

---

### Post by branko.savic on 2010-09-02
I tried the alternate cd on a USB stick and it seems to load just fine, I get into the setup and I get to choose language and keyboard, after that it says that there is no cd in the drive and the installation aborts!

Shouldn´t it be able to install from a USB stick, or do I really have to burn it just to try if it works?

---

### Post by gypsumwolf on 2010-09-02
> **branko.savic said:**
> I tried the alternate cd on a USB stick and it seems to load just fine, I get into the setup and I get to choose language and keyboard, after that it says that there is no cd in the drive and the installation aborts!

Shouldn´t it be able to install from a USB stick, or do I really have to burn it just to try if it works?

I am not sure on that one. I have only used CD's for that. 

Although,
I am pretty sure I have used the **Minimal CD with USB**, maybe you should try that. [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

