---
title: "Ubuntu 10.04 freezes after booting"
date: 2010-06-22
forum: General Help
---

### Post by dsfsp on 2010-06-22
I have been using Ubuntu 10.04 since it was released.  Over the last couple of days, I installed a number of applications recommended by different websites, and seem to have corrupted the system somehow.  

Now, whenever, I boot into Ubuntu, the boot sequences proceeds normally until the desktop appears, after which the screen freezes and I am unable to click on anything (although the mouse cursor moves about all right).  At this point, on the screen, I have the applet for my recently installed 'Gnome Do' application, and the dialogue box asking for the 'login keyring'.  Since the latter used to appear earlier also, i presume that the problem might be related to Gnome Do.  

However, since I am absolutely unable to do anything from this point on (can't click on menus, etc), I don't know how to uninstall Gnome Do.  I inevitably have to press Ctrl-Alt-F1 to go to Terminal, and then do a sudo-reboot.  Thankfully, I do have a dual-boot Windows XP on the same machine, from where I am posting this.  

Can anyone help me get back into my Ubuntu?  Right now, it has become completely unusable.  Needless to say, I am quite a noob at this...

---

### Post by wilee-nilee on 2010-06-22
How would we help you when you are giving really no details, what did you install and from where before this problem started. Is this a install from a live windows enviroment=wubi.

---

### Post by dsfsp on 2010-06-22
Hi Wilee-Nilee!  Sorry for being too summary earlier.  I had installed the software packages from the Synaptic Package Manager within Ubuntu.  From what I recall, I installed a program called 'dock' or 'docky' which gives a Mac like dock on the desktop to start applications.  I also installed Adobe Reader for linux, and this 'Gnome Do' application.  All of them were installed from within Ubuntu, not from a 'windows live environment'.  

Basically, I just want to be able to some sort of a 'system restore' on ubuntu to a couple of days earlier, if possible.  But since the screen hangs after rebooting, I am unable to do anything.

---

### Post by wilee-nilee on 2010-06-22
> **dsfsp said:**
> Hi Wilee-Nilee!  Sorry for being too summary earlier.  I had installed the software packages from the Synaptic Package Manager within Ubuntu.  From what I recall, I installed a program called 'dock' or 'docky' which gives a Mac like dock on the desktop to start applications.  I also installed Adobe Reader for linux, and this 'Gnome Do' application.  All of them were installed from within Ubuntu, not from a 'windows live environment'.  

Basically, I just want to be able to some sort of a 'system restore' on ubuntu to a couple of days earlier, if possible.  But since the screen hangs after rebooting, I am unable to do anything.

What I mean from a live windows environment is this a wubi install, did you install Ubuntu from a live widows setup. 

Many people use the term dual boot and this throws off others when a wubi install is a pseudo dual boot, it just helps to know whats up. If you can get to the recovery section of grub 2nd line you can get to a command terminal and just run ```
sudo apt-get remove gnome-do
``` It might be the docky setup who knows.

What is your computer model?

---

### Post by dsfsp on 2010-06-22
> **wilee-nilee said:**
> What I mean from a live windows environment is this a wubi install, did you install Ubuntu from a live widows setup. 

Many people use the term dual boot and this throws off others when a wubi install is a pseudo dual boot, it just helps to know whats up. If you can get to the recovery section of grub 2nd line you can get to a command terminal and just run ```
sudo apt-get remove gnome-do
``` It might be the docky setup who knows.

What is your computer model?


Hey thanks!  I was able to get rid of Gnome-Do with that terminal command you provided.  [I am quite lost on Command Line interfaces, so didn't realise that one could get uninstall a program so easily!]  Everything seems to be back to normal now.  Many thanks!!!  :)

Reg the 'live windows' thing, I have actually had Ubuntu on this system for nearly a year.  I had initially installed it using a Live CD, but going for a full install instead of running it off a CD.  Later, I just upgraded it to version 10.04 from within Ubuntu.

 Not sure what a wubi install is, but by 'double boot' I meant the sort of system I have, where the GRUB menu gives me the option of either booting into Ubuntu or Windows while starting the machine.

---

### Post by wilee-nilee on 2010-06-22
> **dsfsp said:**
> Hey thanks!  I was able to get rid of Gnome-Do with that terminal command you provided.  [I am quite lost on Command Line interfaces, so didn't realise that one could get uninstall a program so easily!]  Everything seems to be back to normal now.  Many thanks!!!  :)

Reg the 'live windows' thing, I have actually had Ubuntu on this system for nearly a year.  I had initially installed it using a Live CD, but going for a full install instead of running it off a CD.  Later, I just upgraded it to version 10.04 from within Ubuntu.

 Not sure what a wubi install is, but by 'double boot' I meant the sort of system I have, where the GRUB menu gives me the option of either booting into Ubuntu or Windows while starting the machine.

gnome-do was the problem then, glad you got it removed, and your up and running.

---

