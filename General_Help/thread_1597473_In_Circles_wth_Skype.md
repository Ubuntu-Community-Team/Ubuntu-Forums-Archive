---
title: "In Circles wth Skype"
date: 2010-10-15
forum: General Help
---

### Post by Quarkrad on 2010-10-15
There seems to be a common solution to get the webcam working with Skype - rather than launching with **Skype** you launch with **LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype**  - so far so good.  When I do this I get the error  **There was an error launching the application. Details: Failed to execute child process "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so" (No such file or directory)**.  But I do have that directory and file on my system.


 A ubuntu community doc talks about the terminal command **sudo ld.so.preload-manager** when I action this I get
 [B]sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so
[sudo] password for dad: 
sudo: ld.so.preload-manager: command not found[/B]

Not sure what to do now.  (10.10 32 bit)

---

### Post by SteveDee on 2010-10-15
I think the problem you refer to was only an issue on 9.10 with earlier versions of Skype.

If you use the latest Skype version (I think its 2.1.0.81 Beta) then it can be run using the command: skype

---

### Post by Quarkrad on 2010-10-15
I'm running ubuntu 10.10 and Skype 2.1.0.81 Beta for linux.  The issue,and it seems to be an old one, is you can set up and make a call but when you enable the webcam Skype crashes.  If you configure Skype so that the webcam is enabled when you make a call then it crashes as soon as try and connect to the other end.

---

### Post by perspectoff on 2010-10-15
> **Quarkrad said:**
> I'm running ubuntu 10.10 and Skype 2.1.0.81 Beta for linux.  The issue,and it seems to be an old one, is you can set up and make a call but when you enable the webcam Skype crashes.  If you configure Skype so that the webcam is enabled when you make a call then it crashes as soon as try and connect to the other end.

Don't say "you". That doesn't happen with my equipment. Skype works flawlessly for me.

---

### Post by Quarkrad on 2010-10-15
wow - that's great.  I have two set ups, my own and a friends who I talked into Ubuntu.  My machine is a 32 bit Desktop running 10.10 with an old Logitech Quickcam webcam - the other is an old 32bit intel (855) laptop running 10.10 with a more up to date Logitech Quickcam webcam.  On both machines the webcams work 100% in Ubuntu - it's just when they operate via Skype.   I could try putting the newer webcam on my Desktop.  In terms of s/w both machines are the same.  Thanks for your post - it's nice to know somebody has it working.

---

### Post by SteveDee on 2010-10-15
I've just tested Skype on my laptop running 10.10 and tried both conditions you describe, but its working fine.
But I am using an earlier kernel due to a different problem (see: [http://ubuntuforums.org/showthread.php?t=1593960&page=2](http://ubuntuforums.org/showthread.php?t=1593960&page=2))

---

### Post by no2498 on 2010-10-15
is he missing the 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
file

---

### Post by Quarkrad on 2010-10-16
Now it works (almost) on both machines.  On the laptop (the important one) it works but on the 'incoming' video screen there is a small white rectangle within the window - it isn't very big but annoying.  I'm sure I've read about this before in other blogs - any ideal what could be causing this?

---

### Post by cocokessler on 2010-10-16
> **Quarkrad said:**
> Now it works (almost) on both machines.  On the laptop (the important one) it works but on the 'incoming' video screen there is a small white rectangle within the window - it isn't very big but annoying.  I'm sure I've read about this before in other blogs - any ideal what could be causing this?
Quarkrad, 

What exactly was the change you made to get it (almost) working on your machines?

---

### Post by Quarkrad on 2010-10-16
To be honest nothing - it seems that it didn't work on day but did the next.  I do remember doing a _complete_ removable of Skype via Synaptic, rebooting and then installing Skype from the Skype web site and rebooting again.  Then, apart from this small white rectangle, it all worked.  Strange - I hope it continues to work!

---

