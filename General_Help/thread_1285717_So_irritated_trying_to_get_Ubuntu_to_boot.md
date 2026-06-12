---
title: "So irritated trying to get Ubuntu to boot"
date: 2009-10-08
forum: General Help
---

### Post by linewire on 2009-10-08
I made the switch over to Linux from Windows and so far nothin but problems with my video driver (which I can handle). overall I like it alot more than Windows...BUT, I was forced to hit the restart switch when my comp hung after sleep mode.

Now when I tried to log in I got all these erros and had to start in low res mode, so I install the drivers again and BAM, system says no drivers installed...so I install a diff set of drivers and now when the login screen comes the screen is full of white noise and I can't do anything or see anything.  Any help would be GREATLY appreciated.

---

### Post by Peter09 on 2009-10-08
OK - get into recovery mode by hitting escape at the grub prompt and selecting (using the arrow keys) the second from the top option. Boot that by hitting enter.

You should come to a menu, one item of which is to reconfigure your video drivers. Try that.

---

### Post by linewire on 2009-10-08
Thanks for the reply.

I have done the recovery but no luck with anything in there. (Used auto fix video)
Is there a way I can set the "Device" part of the Xorg.conf file to default from the command line?  Using 9.04

---

### Post by Peter09 on 2009-10-08
Do the recovery mode bit again, in the menu there is an option to go to command prompt.

From there you can issue terminal commands.

I would suggest you do these first.

```
sudo apt-get update
``````
sudo apt-get upgrade
```you can get to your xorg file by

```
nano /etc/X11/xorg.conf
```however I would first try the other methods. What version of Ubuntu are you running?
EDIT just noticed that you are on 9.04 - make sure you do all the upgrades

---

### Post by CharlesA on 2009-10-08
What card do you have and how did you go about installing the drivers?

I had to use envy-ng to get the drivers to install correctly on my box running an nvidia 9400GS.

When I tried to use hardware drivers, it would download and "install" them, but it wouldn't actually install them.

---

### Post by linewire on 2009-10-08
when trying to open /etc/x11/xorg.conf or even goto /etc/x11 it says the folder doesnt exist X_X.

I have a ati 4870.  I use Envyng first which resulted in a horribly laggy system, then I installed using the "manual" install and it worked great but then had to restart the comp and bam it wouldnt work with manual install so I tried the standard ati install via their .run file and now i cant boot : (

---

### Post by Peter09 on 2009-10-08
the folder is
> 
/etc/X11/

note that case matters

---

### Post by cariboo on 2009-10-08
I would suggest booting from the Live CD and running fsck, that would have fixed your problem if you had done it right from the start, without having to try all sorts of other things.

Sometimes it is better to relax and take a few minutes to see if anyone has run into similar problems, than it is to jump right in and try and fix the problem.

---

### Post by linewire on 2009-10-08
So far I have tried 4 alternative methods to fix this but I get the same 3 flicker screen and then a frozen screen.  

Am I able to just reinstall Ubuntu without erasing everything like I did with Windows?

---

### Post by linewire on 2009-10-08
Got it following some instructions that I can't seem to find the source of now.

from command line:

sudo sh /usr/share/ati/fglrx-uninstall.sh
 
 
 sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
 
 
 
 sudo dpkg-reconfigure -phigh xserver-xorg

i can now access my desktop again! Thanks to all the replies.

---

