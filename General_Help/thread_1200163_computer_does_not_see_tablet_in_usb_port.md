---
title: "computer does not see tablet in usb port"
date: 2009-06-29
forum: General Help
---

### Post by ailidhe on 2009-06-29
I'm new to linux (upgraded ubuntu today from 8 to 9) and I want to figure things out by myself but getting my trust tb-2100 to work is just too much for me.

I've tried several howto sites and my computer won't recognize the bloody thing. I plug it in a working usb port and all I see is my normal mouse, not my tablet, it just won't show up.

Do I have to install something first? And no, it is not broken, it was working yesterday on another computer and the light is flashing.

Thanks

---

### Post by Favux on 2009-06-29
Hi ailidhe,

First you're going to have to figure out which actual tablet type you have that has been rebranded by trust.  Then you'll probably need to install the drivers.

The following two links show you ways to determine the tablet:
[http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
and then the aiptek wiki:
[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

You may also need to modify or add a .fdi

Good luck!

---

### Post by ailidhe on 2009-06-30
Thank you for your answer, I've been working on it and all I need to do now is put the fdi file in /etc/hal/fdi/policy/

The problem is, I can't seem to figure that out either. I know I should start at the beginning and read everything but I must finish a project for work tomorrow and I need the tablet for it.

If anyone can help me before that time, thanks. I think I need to do the sudo thing to be able to write in the folder, but the terminal keeps telling me I'm a n00b.

---

### Post by Favux on 2009-06-30
Hi ailidhe,

You should be able to:
```
gksudo gedit /etc/hal/fdi/policy/"the name of your .fdi file"
```
It should open an empty file.  Copy and paste the contents of the .fdi you have into it.  Save.  Reboot.

If you get the tablet working when you get a chance please post what you did.

---

### Post by ailidhe on 2009-07-01
I've got it working :) YAY!.  Ok, most of the guides are good, but I found a few problems:  

1. If you install anything before installing one language properly, the installation may not succeed. 

2. Install the diver for aiptek from the synaptic package manager. I tried everything to install it manually, but my computer wouldn't accept it for some strange reason, but instead made everything on my desktop vanish.  

3. This is optional and not suggested. Buy a new tablet 2 hours before you got the old one working.

---

### Post by fragos on 2009-07-01
You didn't say which Ubuntu version you're running. On older versions my Wacom USB tablet would only be recognized if plugged in before booting. Depending on which Ubuntu version you're running you may have to do some xorg.conf editing. Ubuntu 9.04 uses HAL to discover devices and for my Wacom, no xorg.conf editing was required.

---

### Post by Favux on 2009-07-01
Hi ailidhe,

Great!  Good job.  I hope you can return the new tablet, if you want to.

So:
1) From the links above you determined that your trust tb-2100 tablet was a rebranded Aiptek.
2) You used the Aiptek driver in the Jaunty repository, installing it with Synaptic Package Manager.  (Do you know the driver version number?)
3) You added a 10-aiptek.fdi to "/etc/hal/fdi/policy/".

Could you please tell me the contents of the 10-aiptek.fdi?  I ask because apparently your stylus buttons weren't working and now they are (?).

Actually the Aiptek driver package should install a 10-aiptek.fdi for you.  I don't know why it doesn't.

---

### Post by zasq on 2009-07-16
Hello,

I have the same problem - my graphic tablet (a medion md 85637 USB P82012, supposed to be the same as the Aiptek SlimTablet 600U) is not recognized (not even with lsusb). And there is no file 10-aiptek.fdi. Could you tell me the contents of that file, so I can create and edit it manually?

These are the packages I have installed:
wacom-tools 10.8.2.2
xserver-xorg-input-wacom 10.8.2.2
xserver-xorg-input-aiptek 1.1.1.1.

I have jaunty 9.04 with kernel 2.6.28-11-generic (I used to have the newer 2.6.28-13-generic kernel, but that one broke all my usb-devices). 

The tablet was recognized before, but since I upgraded and then downgraded the kernel again, it doesn't work anymore.

Hope someone can help. Thanks!

---

### Post by Favux on 2009-07-16
Hi zasq,

The Aiptek package doesn't install the .fdi for some reason.  We have a modified version on post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=5](http://ubuntuforums.org/showthread.php?t=1191826&page=5)  We've been working on fuctionality.  I think the original is on or linked in the first page or two.  If not you can find it around.

---

