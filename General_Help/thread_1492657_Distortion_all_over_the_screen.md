---
title: "Distortion all over the screen?"
date: 2010-05-25
forum: General Help
---

### Post by Eulogy69 on 2010-05-25
Hey, Just got Ubuntu 10.04, Ive had some experience before with it but this is the first time I have completely removed Windows (7) from my system....

Okay, short and sweet, I have a Gateway Lt31 series netbook, It has a {Ati X1200 Graphics/video card}.  I get really bad distortion on the top of my screen at all times, and at others the entire screen becomes Distorted.  Sometimes the text becomes no mre than mere blurs and I cant see particular letters ( I cant see the "v,n, or o" right now).

Im downloading the 9.10 iso now and will downgrade if necessary, But I would really love the help.

All help is appreciated, I look forward to working with Ubuntu and Ubuntu forums :) 
Peas.

---

### Post by Eulogy69 on 2010-05-25
Okay, I could`nt fix it, Got 9.10, going to have to wait for a more stable distro. 
:(

---

### Post by alex.wifiguy on 2010-06-06
I too have a Gateway Lt31 (radeon x1200) with loads of distortion/graphics problems under Lucid Lynx. At first only while using 3d acceleration then all the time. I managed to fix it by
adding nomodeset to my grub configuration.
Here's how to do it if you're using grub2, If on 10.04 you probably are.

sudo gedit /etc/default/grub
Locate GRUB_CMDLINE_LINUX="" and add nomodeset so it looks like this
GRUB_CMDLINE_LINUX="nomodeset"
Save the changes then update grub
sudo update-grub
and reboot.

---

### Post by Lennon V C on 2010-06-17
> **alex.wifiguy said:**
> I too have a Gateway Lt31 (radeon x1200) with loads of distortion/graphics problems under Lucid Lynx. At first only while using 3d acceleration then all the time. I managed to fix it by
adding nomodeset to my grub configuration.
Here's how to do it if you're using grub2, If on 10.04 you probably are.

sudo gedit /etc/default/grub
Locate GRUB_CMDLINE_LINUX="" and add nomodeset so it looks like this
GRUB_CMDLINE_LINUX="nomodeset"
Save the changes then update grub
sudo update-grub
and reboot.

Thanks I will try it out.

---

### Post by Eulogy69 on 2010-10-27
> **alex.wifiguy said:**
> I too have a Gateway Lt31 (radeon x1200) with loads of distortion/graphics problems under Lucid Lynx. At first only while using 3d acceleration then all the time. I managed to fix it by
adding nomodeset to my grub configuration.
Here's how to do it if you're using grub2, If on 10.04 you probably are.
 
sudo gedit /etc/default/grub
Locate GRUB_CMDLINE_LINUX="" and add nomodeset so it looks like this
GRUB_CMDLINE_LINUX="nomodeset"
Save the changes then update grub
sudo update-grub
and reboot.
 
Thanks, and sorry for the verry late reply. Ill try this out shortly and will post the results. :)

---

### Post by morrie on 2011-03-30
I have an LT31 (LT 3103u).  Just tried the Netbook Remix, after 10.10 froze my computer.  The remix seemed to fix the problem, but there was extreme graphics distortion.  I downloaded the Crack Pusher ATI drivers, that only helped a little.  Then I tried the "nomodeset" fix, by editing the GRUB file.  Not sure what this does specifically, but I am back to where I started. (I also got an error that Unity was unable to find a driver that it neeed?). Ubuntu appears to boot and login (with clean screen) but then freezes (might have something to do with wifi, as that won't light up at the switch.

---

### Post by 3Miro on 2011-03-30
You have an old ATI video card and those have virtually no Linux support (new ATI cards are OK).

Don't use Unity, just try using the laptop without any visual effects, this will hopefully make things usable.

---

### Post by morrie on 2011-03-30
Thanks, but I have to let you all know that it was only MY FIRST REBOOT since changing GRUB to "nomodeset" that froze the computer and kicked that error (that "unity" error looked too unrelated to be repeatable). 

I restarted the computer **one more time**, and everything was great :D !  I have been testing it for a couple of hours now _without a glitch_.  Streams online video just fine. So far everything works! (Have to get back to you on Unity, which I am sure is fine, but I am new to it).

Remember, I tried _both_ of the above remedies, so it might be that you need to do both of them in order to obtain my result.

Enjoy!

---

### Post by morrie on 2011-03-30
In regards to ATI video cards, I think some recent retroactive projects have changed the Linux/ATI scene of late..   I have an old Pentium M laptop with a mobility Radeon 7000 (which is pretty darned old, right)?  I remember I had to do some forum-grubbing, but it wasn't that hard to get that thing going.  (I use it still, all the time for streaming online shows-Ubuntu 10.04LTS). 


 I do agree that it could be SO much better, but so far, I am 2 for 2 on these. :)

---

