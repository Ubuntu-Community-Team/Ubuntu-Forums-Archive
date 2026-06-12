---
title: "Ubuntu won't start :("
date: 2010-07-17
forum: General Help
---

### Post by auramaster on 2010-07-17
I hope this is the right place to post this.

I just got an Asus UL80VT-A2, and was working with PowerTOP when I accidently disabled all non-media USB objects, including my mouse. Google said it went away after restarting, but when I restarted, Ubuntu wouldn't work. The screen stays blank no matter how long I leave it on, and briefly shows the Ubuntu logo when I turn it off. The Windows 7 that came with it works fine.

I suspect it has something to do with an Nvidea graphics driver I was asked to install, since it had to restart to work. Does anyone know for sure what's causing it, and how to fix it? I really don't want to have to reinstall Ubuntu and start over.

---

### Post by quixote on 2010-07-19
I'm not sure of the answer to your question, so this is mostly just to bump you back up the question queue again.  I don't know what PowerTOP is, or how you'd re-enable non-media USB objects.

Sounds like what's happened is your X windowing system (ie the graphical GUI) messed up with the driver. The steps to fix it are going to be, more or less, boot into recovery console, install the right driver for your card, possibly check /etc/X11/xorg.conf for any necessary changes.  It's quite likely this can be fixed without reinstalling, so don't lose hope :D.

A few things to do while you wait for a better answer: boot into recovery mode.  If the grub menu is hidden, press Shift at the beginning of boot up to show the menu.  Have the computer connected via ethernet.  When recovery mode starts coming up, select "root access with networking".  If you already know your graphics card model, note it in your response.  If not, you can find out with ```
lspci | grep 'VGA'
```

And then, just on the off chance it'll help, you can try to fix broken packages:```
dpkg --configure -a
```(You don't need "sudo" first because you're already root.) Then reboot by typing "reboot" (without quotes) at the command prompt.

For what it's worth, if you have nvidia graphics, and you're running Lucid, the nouveau (open source) nvidia driver is better than nvidia's own proprietary ones.  Really! I wouldn't recommend doing the following until we know it's right for your graphics setup, but I'm including the command in case you can use it later. That driver can be installed by using ```
apt-get install xserver-xorg-video-nouveau
``` (Again, prepend sudo if doing this in normal, not recovery mode.)

---

### Post by auramaster on 2010-07-24
Ahhh!!!!! Sorry for bumping, but if I didn't, I would just make a new identicle thread because after reinstalling Ubuntu, MY COMPUTER BROKE ITSELF AGAIN!!! Just got my laptop a week and a half ago, and its broke itself three times.

This time, I have no idea why. It was working fine, then suddenly the screen wouldn't come up again, just like before. However, I didn't install a new driver or do anything that would mess it up. As much as I appreciate quixote's advice, recovery mode won't let me use any commands. Is there any way I can stop this from happening, and preferably fix it without recovery mode? I do have a Live CD, if it helps.

---

### Post by wired99 on 2010-07-24
I had a somewhat-maybe-not-so-similar experience when I first installed Ubuntu. It would not recognize my mouse or keyboard but it ran Windows just fine.

I discovered that the BIOS was setup to only allow a Windows system. Once I selected to allow "other" systems everything went fine.

---

### Post by MooPi on 2010-07-24
I've just read a review of your laptop model and surmise the problem could be the two distinct GPU's installed. The Intel 4500 and Nvidia's G210M. Is there a way to disable one GPU in the bios and use just one of the GPUs instead of the tandem setup ?

---

### Post by auramaster on 2010-07-24
There is a way to disable one of them (why didn't I think of that?), but I'll have to reinstall Ubuntu and disable it before it acts up again. Unless someone else has a better idea, I'll do that later tonight. Thanks to everyone who's responded!

---

