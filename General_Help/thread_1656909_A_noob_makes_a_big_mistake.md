---
title: "A noob makes a big mistake"
date: 2010-12-31
forum: General Help
---

### Post by Myfathersheart on 2010-12-31
Ok I have a MSI a6000 Laptop
Pentium Dual Core
3g ram around 2.8ghz (I think)
nVidia GeForce 8200m G
It came pre installed with windows 7

This laptop is known for having Ubuntu installation issues.  I think it is because of the nVidia chip.  In order to boot Ubuntu you have to use a CD or USB drive and set nomodeset before loading ubuntu. 

I figured this out after many trial and error runs to get Ubuntu running (by the way this is my first linux install and as far as computers go I'm a total noob). 

Once Ubuntu was running of the CD I attempted to install it.  It didn't give me the option to dual boot install alongside windows. I either had to set the partitions myself or wipe the whole hardrive and install.  I tried to partition it myself (big mistake)  I accidently changed a partition to "linux swap" (the partition was there already on my computer from factory it was a 104mb partition). After doing that I did not finish my Ubunut install I tried to go back to windows 7 and my computer booted up and said "error: no operating system installed."  Then I tried recovery from cd and f3 recovery... neither worked. They both said they worked but the "error: no operating system installed" kept coming up after turning on my computer. 

So I realized my computer may be screwed and decided to just go boot Ubuntu from disk (in nomodeset) then actually install Ubuntu and partition the hardrive with a /home partition.  I followed a how to online to do this.  I had three partitions one was ext4 journaling mounted on /  another was a 2g linux swap the third was a ext 4  journaling /home.  The installer said the installation was complete and asked me to reboot.  I rebooted and took the CD out after hitting "reboot" (dont know if that was a mistake or not).  After this restart my computer would not run windows (still obviously) and it would not run Ubuntu either. Ubuntu gets stuck on the Logo screen with the four dots. And (of course) windows is gone. 

I figure that Ubuntu won't boot because it won't let me set nomodeset.  Maybe I am wrong though.
(Ubuntu will not boot from a CD either and no matter how I try to boot Ubuntu the "keyboard" logo will not appear so I can't access the menu where I previously choose to use nomodeset)

So essentially I cant run either operating system on my computer.  What the heck do I do?

---

### Post by nitro_n2o on 2010-12-31
if you do not have something sensitive on the machine, I'd suggest wiping it all out and starting from scratch 

make sure you read one of the tutorial on dual boot, for example this one [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

read carefully and you'll be fine, good luck :)

---

### Post by IWantFroyo on 2010-12-31
Ask your manufacturer for a Windows recovery cd. According to Microsoft, you have a right to one, even if it doesn't come with the laptop. So do that, now install Windows OVER YOUR WHOLE HARD DRIVE! So then what you do, is you boot into Windows, put in a Linux cd, go to My Computer, and select the Ubuntu icon, then install Ubuntu within Windows (if you have a firewall, let pyrun access the WWW). Then reboot, and you'll get options to boot into either Ubuntu or Windows. If you REALLY want to, you can partition the hard drive with something like GParted, but this is finicky and unnecessarily complicated.
Hope this helped!

---

