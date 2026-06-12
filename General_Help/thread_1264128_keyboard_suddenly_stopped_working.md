---
title: "keyboard suddenly stopped working"
date: 2009-09-11
forum: General Help
---

### Post by Maerwyn on 2009-09-11
Hi, I have a bit of a problem. 

I have been running Kubuntu for quite a while now and any issues I've come across I've been able to solve on my own via these forums. Tonight, seemingly out of nowhere, my keyboard stopped working. The mouse worked fine. I restarted several times and applied the waiting system updates. These did not help. I plugged in a new keyboard, which I know works, and still nothing. So far I've tried both a PS2 keyboard and a USB keyboard. (I am using my husband's computer to type this message.)

Everything worked fine up until about 2 hours ago. Any help is greatly appreciated.

---

### Post by Bucky Ball on 2009-09-11
My mother-in-law had the same problem. This was a total fluke but I fixed it by trying this. Open a terminal (Applications->Accessories->Terminal) and paste this in:

```
sudo nano /etc/X11/xorg.conf
```Now add the line in bold to the xorg.conf file under the section regarding keyboard:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        **Option         "CoreKeyboard"**
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
```Your xorg.conf might look a little different to this but doesn't matter. See if that makes a difference. It cured her problem. Her USB keyboard would stop working at boot but when she unplugged and plugged back in it would work again.

PS: If you want to be absolutely fails-safe in case you accidently screw your xorg.conf, make a back up with this code:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```There is also usually a setting for your keyboard in the BIOS. If you are running Windows, do you have the same problem there?

---

### Post by Maerwyn on 2009-09-11
Thank  you for that idea, but Enter doesn't work in the terminal, and I can't type my password because the keyboard isn't working.  Any other thoughts?  (And we're not running Windows.)

---

### Post by VipX1 on 2009-09-11
There is a on screen keyboard in Ubuntu under the disabled access facilities. Look it up in community documentation under the support page. 
I am using Mint so I can't tell you where it is exactly but use that to do what you have to.

---

### Post by Maerwyn on 2009-09-11
Great suggestion, but the Kubuntu virtual keyboard doesn't work in the terminal on my computer.  I'm out of ideas.

---

### Post by Bucky Ball on 2009-09-11
Do you get the same problem if you boot from the LIVE CD?

---

### Post by Maerwyn on 2009-09-11
Interesting you should bring this up. On my husband's computer I am currently burning a live cd to test this out! I don't have any OS disks lying around otherwise I'd have tried this sooner. 

I am planning on reinstalling unless the keyboard doesn't work when I try. 

Thanks for all your help!

-M-

---

### Post by Bucky Ball on 2009-09-12
Pleasure. If you can get it working from LIVE CD, add that line I suggested before to the keyboard section of your xorg.conf.

---

