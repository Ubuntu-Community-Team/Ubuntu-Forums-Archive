---
title: "menu.lst files displays nothing"
date: 2010-10-11
forum: General Help
---

### Post by dimsci_x on 2010-10-11
When i try to edit the 'Menu.lst" file it shows up as a blank file.  I've tried using several editors and commands under the root account.:confused:

using 10.04.1 on HP DV6-2190us laptop

---

### Post by andrewthomas on 2010-10-11
That was with grub legacy (0.97)  With grub2 the file is grub.cfg and is not editable.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by alphacrucis2 on 2010-10-11
> **dimsci_x said:**
> When i try to edit the 'Menu.lst" file it shows up as a blank file.  I've tried using several editors and commands under the root account.:confused:

using 10.04.1 on HP DV6-2190us laptop

Grub2 doesn't use menu.lst

---

### Post by oldfred on 2010-10-12
Some more links that cover just about anything. What is it you want to do so we can direct you to the specific solution.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

### Post by dimsci_x on 2010-10-12
Thanks for the help.  But what is the easiest way to change the boot device order.  im dual booting windows 7 and ubuntu

---

### Post by dimsci_x on 2010-10-12
sorry didnt see last post...i'll try those out.thanks for the help

---

### Post by oldfred on 2010-10-12
If all you want to do is change boot order:

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even grub2.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

