---
title: "Boot screen Ubuntu logo has low resolution and is big !"
date: 2010-07-03
forum: General Help
---

### Post by user1001 on 2010-07-03
Hi,

Firstly when I first installed Ubuntu on my machine, the bootscreen logo was small and high resolution, and it looked nice, however as I started using Ubuntu I must have done something for it to change to large and low resolution.

I try the live cd again and that one is normal, so it must be my settings.. and also when I am shutting down, the screen shows some messages I can't read because it's kind of fast, and the messages are kind of low res too.

Any help?

Thanks =)

---

### Post by philinux on 2010-07-03
> **user1001 said:**
> Hi,

Firstly when I first installed Ubuntu on my machine, the bootscreen logo was small and high resolution, and it looked nice, however as I started using Ubuntu I must have done something for it to change to large and low resolution.

I try the live cd again and that one is normal, so it must be my settings.. and also when I am shutting down, the screen shows some messages I can't read because it's kind of fast, and the messages are kind of low res too.

Any help?

Thanks =)
You probably activated your graphics card driver. What card you using.

See the General Help forum sticky.

---

### Post by user1001 on 2010-07-03
> **philinux said:**
> You probably activated your graphics card driver. What card you using.

See the General Help forum sticky.

I did indeed =) I am using Nvidea Gforce 6600

I'll look at the sticky as well

---

### Post by celldweller1591 on 2010-07-03
Try this, open terminal and type :-
> sudo gedit /etc/default/grub Inside the menu, find the line :- > GRUB_CMDLINE_LINUX_DEFAULT and replace it with > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"  Save,exit and restart.Worked for me! See if that works for you . 
NOTE: Be careful, make backup of the actual line before any editings :)

---

### Post by philinux on 2010-07-03
celdweller, Yes that is in the sticky too via the link under Bootup/Plymouth.

---

### Post by user1001 on 2010-07-03
well this did not work for me :S

---

### Post by Krovas on 2010-07-03
> **user1001 said:**
> well this did not work for me :S

Nor me. Personally, I just deleted all the Plymouth themes except for the text-only theme. But then again, I'm easy to please =)

---

### Post by krishnandu.sarkar on 2010-07-03
Guys try this....It worked for me. [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by doixanh on 2010-07-03
Try [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") tutorial guys :D

---

### Post by celldweller1591 on 2010-07-05
> Yes that is in the sticky too via the link under Bootup/Plymouth. apologies..didnt saw it :) ..

---

### Post by user1001 on 2010-07-06
None of the links helped, I tried all of them, no error or anything, all the commands work but they don't fix the problem :\

---

### Post by krishnandu.sarkar on 2010-07-08
> **user1001 said:**
> None of the links helped, I tried all of them, no error or anything, all the commands work but they don't fix the problem :\

Did you tried this??? [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

This one solved my problem.

---

### Post by bigsmitty64 on 2010-07-08
> **krishnandu.sarkar said:**
> Guys try this....It worked for me. [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

+1 for this!

---

### Post by user1001 on 2010-07-08
> **krishnandu.sarkar said:**
> Did you tried this??? [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

This one solved my problem.

Yes I did, it only changed the resolution of the grub menu :\ :( I am giving up Ubuntu.. it is really tiring me, I'd love to use it but it's not user friendly at all, all it gives you are problems and problems. :(

---

### Post by talz13 on 2010-07-08
> **user1001 said:**
> Yes I did, it only changed the resolution of the grub menu :\ :( I am giving up Ubuntu.. it is really tiring me, I'd love to use it but it's not user friendly at all, all it gives you are problems and problems. :(

You're giving up on ubuntu because the boot screen is slightly larger and slightly fuzzy?

---

### Post by Dead_$partan on 2010-07-08
> **krishnandu.sarkar said:**
> Did you tried this??? [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

This one solved my problem.

I have had limited success with this.  It helped increase the resolution to that stated on the how to but my monitor resolution is 1920x1080 so it still looks pretty pants, plus the logo doesnt fill the screen - there is a black border all the way around.

I have tried subbing the resolutions with 1920x1080 but it doesnt make a difference.

Does anyone know why it affects the boot slash in the first place?  And why these extra packages must be installed as a work around?  I have only found guides that tell you what to do, not why you need to do them, I have never understood why updating grub settings is supposed to help improve the visual appearance of Plymouth

---

### Post by rahilm on 2010-07-08
Any chance that someone knows how to change the resolution of the login screen??
for more info:
[http://ubuntuforums.org/showthread.php?t=1466679](http://ubuntuforums.org/showthread.php?t=1466679)

---

### Post by krishnandu.sarkar on 2010-07-09
> **talz13 said:**
> You're giving up on ubuntu because the boot screen is slightly larger and slightly fuzzy?

Then lastly give a try to start-up manager. sudo apt-get install startupmanager. You can change everything using UI. No tutorial would be needed.

---

### Post by krishnandu.sarkar on 2010-07-09
> **rahilm said:**
> Any chance that someone knows how to change the resolution of the login screen??
for more info:
[http://ubuntuforums.org/showthread.php?t=1466679](http://ubuntuforums.org/showthread.php?t=1466679)

Read the whole thread. There are many methods which are already given. Try those and post feedback whether any of them solved your problem.

---

