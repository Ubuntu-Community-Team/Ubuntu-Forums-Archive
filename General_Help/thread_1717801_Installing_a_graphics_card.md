---
title: "Installing a graphics card"
date: 2011-03-30
forum: General Help
---

### Post by rickygk on 2011-03-30
Hi, I'm running Ubuntu 10.10 on what used to be a  windows vista. I bought me a new graphics card today so that I could  run dual screen (GeForce210). I saw a guide at [http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat) and I followed it.
 I typed: sudo apt-get install nvidia-current
 then I restarted my computer, once again as instructed I typed:
 sudo nvidia-xconfig
 then logged out as instructed...
 After I logged out the screen went black and i was not able to log  in. So I restarted my computer. Now when I turn on my computer I am  getting this error and it's stopping at it.
*********************************************************************************************************
fsck from util-linux-n/g 2.17.2
/dev/sda1: clean, 255658/294092280 files, 5031534/117616640 blocks
*starting apparmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 *setting sensors limits
Starting GNUstep distributed object mapper: start-stop-daemon: unable to stat /usr/bin/gdomap/ (no such file or directory)
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
*starting the winbind daemon winbind
*********************************************************************************************************
 It stops on this screen. I have a lot of school work and projects  that are due very soon on my computer, I do not want to wipe it but I  cannot get it started. If some one knows anything I could do to get past  this I would very much appreciate it.
 I do have an external hard drive and at the moment I am using my  Ubuntu disc to "try Ubuntu" I was going to try backing up everything I  have but it will not let me access root because i am not logged on to  that user, is there anything I can do to get pass this? Any help would  be very much appreciated i cannot lose all this work. I've called around  and no one is willing to work on my computer since it is now running on  Ubuntu 10.10

---

### Post by 3Miro on 2011-03-30
You should be able to boot into failsafe mode. Do that either from Grub (when you chose Ubuntu or Vista) or if you don't get a menu, then hold down the shift key during boot (right after post).

Once in fail-safe mode:

1. Hit Alt+F2 and type:
```
gksudo nautilus
```
BE VERY CAREFUL as this will let you severely damage your system. Then go to /etc/X11 and look for a file called xorg.conf. Delete this file.

2. Uninstall nvidia-current
```
sudo apt-get purge nvidia-current
```

3. Go to System -> Admin -> Additional Hardware and make sure everything is unchecked (you can keep wireless drivers if you are using any, but anything nvidia or ATI should be disabled).

4. Reboot in regular mode.

5. This is what you should have done in the first place. Go to System -> Admin -> Additional Hardware and enable the proprietary Nvidia driver.

---

### Post by lithopsian on 2011-03-30
What card did you have before?

---

### Post by rickygk on 2011-03-30
I just had what ever was stock in windows vista, I was adding a second one for a dual moniter. I'm at class at the moment but i really appreciate t he help, I have projects due tomorrow and i'm pannicing a bit about it. I'll try what you guys said when I get home.

---

### Post by 3Miro on 2011-03-30
> **rickygk said:**
> I just had what ever was stock in windows vista, I was adding a second one for a dual moniter. I'm at class at the moment but i really appreciate t he help, I have projects due tomorrow and i'm pannicing a bit about it. I'll try what you guys said when I get home.

Oh, wait! You actually have two video cards. Before you do anything tell us what the other video card is first. If it is not also Nvidia, then it will not work.

---

### Post by rickygk on 2011-03-30
I'm not really sure, but I took my computer into "Geek Squad" and they said this one is compatible, However they won't install it for me since i am on Ubuntu

[edit] @3miro, ty for all your help I appreciate it so much! I was seriously worried I was about to lose hundreds of hours of work because I could not figure this out. You are amazing!

---

### Post by rickygk on 2011-03-30
[LEFT]The only thing I don't see is when I go to system/admin/ there is only additional drivers, I don't see additional hardware. When I do drivers it scans for additional ones but does not find any
[/LEFT]
[CENTER]
[/CENTER]

---

### Post by 3Miro on 2011-03-31
> **rickygk said:**
> [LEFT]The only thing I don't see is when I go to system/admin/ there is only additional drivers, I don't see additional hardware. When I do drivers it scans for additional ones but does not find any
[/LEFT]
[CENTER]
[/CENTER]

1. You must have either one video card physically installed on your machine or two video cards of the same brand (like two Nvidia).

2. Make sure you have updated your machine (System -> Admin -> Software Updates, check for updates and then install them).

3. If you have an Nvidia video card and/or some models of ATI, then Additional Drivers should give you a list of proprietary drivers to install.

---

