---
title: "apt-get and the Linux image that will no remove"
date: 2011-12-30
forum: General Help
---

### Post by Graham C Williams on 2011-12-30
Ubuntu 11.10 64 bit.
Grub and Synaptic show a Linux-image (2.6....) as present. I want to remove it.
Synaptic shows the objects properties as having no associated files.
The Linux-image is marked for complete removal. When trying to remove the image the system hangs and I have to crash the system and restart then reconfigure dpkg.
Synaptic will not let me change the image attributes to stop the removal.
In this state I cannot add any new files as apt always wants to perform the image removal (that hangs the system).

Do you have any suggestions?
Happy new Year
Graham.

---

### Post by bluexrider on 2011-12-30
you cannot replace or remove a kernel without having a replacement. do you have more than one kernel currently installed

---

### Post by lolpenguin on 2011-12-30
> **bluexrider said:**
> you cannot replace or remove a kernel without having a replacement. do you have more than one kernel currently installed

He's using Ubuntu 11.10, which uses kernel 3.0.0, so the 2.6.3x kernel used by prior versions of Ubuntu is obsolete.

Make sure you boot into the NEWEST kernel (hold shift before GRUB loads, the select the first one). I suggest using Ubuntu Tweak to remove old kernels.
```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
Launch Ubuntu Tweak, then click on the Janitor tab, the select "old kernel", then select everything, and click "clean".

---

### Post by Graham C Williams on 2011-12-31
I will try tweak and post the results. Sorry, but my reply will not be quick. Have a great new year.
G

---

### Post by Graham C Williams on 2011-12-31
Hi again. 
It is not clear in my notes but I cannot use any technique that uses apt-get because the first thing apt-get tries to do is remove the image - this causes the OS to hang etc etc. For some reason I cannot switch the status of the image away from remove.
I was thinking of trying Aptitude but that is the same, I need apt-get to download it in the first place.
I cannot use Synaptic because it is an interpretation of apt-get.

After all, I'm not sure there is any image file too remove, only the pointer to that image that was once there. Right clicking on the image entry in Synaptic and looking at the properties shows no files associated with the entry...

I hope this makes things clearer.
Graham.

---

