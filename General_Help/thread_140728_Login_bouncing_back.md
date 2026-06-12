---
title: "Login bouncing back"
date: 2006-03-06
forum: General Help
---

### Post by silhouette on 2006-03-06
Hi all,

I'm having a problem logging into Ubuntu. First some context: before this happened, I copied a large quantity of files from the other hard drive I have in my machine to the main drive. After this I found I couldn't open any program -- when I tried to do so, I watched the cursor do its bouncing trick for a while, then all was still as if I'd never told the computer anything. I figured a restart should do the trick, so I watched it shutdown and load everything again. Having come back to the login screen, I entered my information and fired away. The screen went blue (being my desktop background color) and for a minute I thought the KDE loading box would appear.... but I was bounced back to the login screen. I tried logging into GNOME, then GNOME Failsafe, and finally Terminal Failsafe. Terminal Failsafe works but the others don't -- I'm bounced back to the login screen every time. (I haven't tried opening a prompt via the grub screen yet, but I'm sure it would work too.)

I suppose I should add that I don't have Kubuntu installed the "right" way -- I first installed Ubuntu to try out Gnome and then added kubuntu-base, kubuntu-desktop, etc. manually, through Synaptic. This didn't seem to cause any problems, though.

Anyway, I'm still a Linux noob (been using it for the past three weeks), so I'm not too versed on Linux commands just yet, enough to solve this anyway. So... what should I do?

---

### Post by aysiu on 2006-03-06
Do you happen to know if you're using KDM or GDM as your login manager?
Well, we'll assume you have both and cover our bases.

Press Control-Alt-F1.
Log in.
You should be at a black screen with white text that looks like this: ```
silhouette@ubuntu:~$
``` At that "prompt" type ```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
``` Then press Control-Alt-F7 and report back what happened.

---

### Post by feathers on 2006-03-07
Your harddrive may be full.  Change to a text console with ALT -- F1, login and type in the command df -h and look at the figures. If it says that on one partition, only about 1% of space is available, you have to delete files. rm is the command, if you want to delete directories, type rm -R. You may have to be root so type sudo rm -R deletedirectory.

---

