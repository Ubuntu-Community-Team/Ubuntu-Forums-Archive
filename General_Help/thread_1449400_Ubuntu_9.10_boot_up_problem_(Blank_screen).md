---
title: "Ubuntu 9.10 boot up problem (Blank screen)"
date: 2010-04-07
forum: General Help
---

### Post by bobkatevan on 2010-04-07
Hi everybody,

Last night I upgraded from 9.04 to 9.10 in search of faster internet (which I got by the way), but now whenever I try to boot it goes to a blank screen for about 10 minutes befor going to the desktop. Its completely blank and has no cursor or anything. It's a huge problem and I could really use some help. 9.04 never did this.

Thanks in advance

---

### Post by colorlessprism on 2010-04-07
when the computer is booting up you should see "grub Loading", when that is on the screen press esc. highlight the top item on your list and press e. try deleting "quiet" and see if you can tell what its getting caught on. 
you may also be able to look here: **/var/log/boot**

---

### Post by bobkatevan on 2010-04-07
it says"(Nothing has been logged yet.)"
I haven't tried the GRUB menu yet though, I'll get back on that...

Thanks!

---

### Post by bobkatevan on 2010-04-07
Hello again,

I tried deleting quiet in the GRUB menu but it didn't make any difference. The screen was still totally blank. Each boot up takes a good 10 minutes before the black and white ubuntu logo appears. Any more help is really appreciated.

---

### Post by colorlessprism on 2010-04-08
this is a solution to a very old bug:

Open your System / Administration / Screens and Graphics menu and  look at your actual screen resolution.
Type "gksu gedit /etc/usplash.conf" in a terminal  to edit your usplash.conf file and change the resolution to match what was shown in Screens and Graphics.  Save the file.
Type "sudo update-initramfs -u" without the quotes in a terminal to  apply the changes to usplash.

another thing to try would be:
sudo cp /boot/grub/menu.lst /boot/grub/bakmenu
sudo gedit /boot/grub/menu.lst

scroll down until you see somthing like:
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
and do this:
# defoptions=##quiet splash

---

### Post by bobkatevan on 2010-04-08
Ok so I looked and I dont even have the Screens and Graphics menu. I tried installing the ATI driver because i'm running an ATI Radeon X300 as mya grpahics card. This didn't help the boot up though. This problem is really wierd because it takes forever but I eventually get to the desktop adn it works fine. I really need it to boot faster though. I also checked the splash screen and the resolution looked right, I'm not sure if it is though because I couldn't get to the screens and graphics. I'll probably try the quiet splash next...

---

### Post by bobkatevan on 2010-04-08
Ok Never mind. I found the display menu and the splash screen had the correct resolution. I updated it anyway just in case. I also changed that part in the boot menu, I'll restart to see if it helps. Thanks

---

### Post by bobkatevan on 2010-04-08
I'm back again. it may be of some help to know that most of the screen savers wont work either. Some will but alot won't like color flames or antspotlight...

---

### Post by colorlessprism on 2010-04-08
the only thing i can think to do beyond what we've done it this:
sudo dpkg-reconfigure usplash

---

### Post by bobkatevan on 2010-04-08
I'll try that but I think I've got some info thagt could help. Here is how the boot process goes
 
I turn on computer, it starts the GRUB, GRUB finishes loading and the kernel goes to start up. 10 minutes or so later the blank screen goes away and the black and white ubuntu logo and loading bar appears, shortly after the desktop starts up. This makes me think it might not be the spash screen. It also may be inmportant to note that my HDD indicator light is not flashing while the blank screen is up. 
 
Any ideas???

---

### Post by colorlessprism on 2010-04-08
typically before the splash screen is when some basic things are loaded. by deleting quiet. from the boot screen we should have seen some things load up. im not sure if X failing to load is your problem, but i do think it halts for 5 min or so if it does fail. if "sudo dpkg-reconfigure usplash" doesnt fix your problem we may have to wait for more help since it probably has something to do with your ati card.

---

