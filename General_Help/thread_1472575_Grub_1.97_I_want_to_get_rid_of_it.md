---
title: "Grub 1.97 I want to get rid of it"
date: 2010-05-04
forum: General Help
---

### Post by Deuzy on 2010-05-04
I recently dual booted my HP dv6 so as to try out kubuntu (vista is my other OS) and well I need the extra space for the vista partition and would like to remove it. however, after doing some research, I've learned that I should repair my mbr before removing the kubuntu partition. I like kubuntu its nice I just need to have my computer all vista at the moment is all. Any help would be greatly appreciated.

---

### Post by mk1w86 on 2010-05-04
You need to use the Startup Repair utility on your Vista installation disk which will overwrite the MBR. ;)

---

### Post by Deuzy on 2010-05-04
I understand this however, I was unlucky enough to have a recovery partition instead. also, and I don't know if this would've worked or not, but i can't even get to the system recovery part of my computer. Grub takes over and doesn't let it execute.

---

### Post by Leppie on 2010-05-04
to remove grub from your mbr, boot either into the (k)ubuntu install or boot off a (k)ubuntu livecd.
then issue these commands in a terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
if you receive any message/warning while installing lilo, just ignore it and continue.

rebooting should take you straight into your windows install.

---

### Post by mk1w86 on 2010-05-04
You can get a Vista recovery disk from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by dino99 on 2010-05-04
> **Leppie said:**
> to remove grub from your mbr, boot either into the (k)ubuntu install or boot off a (k)ubuntu livecd.
then issue these commands in a terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
if you receive any message/warning while installing lilo, just ignore it and continue.

rebooting should take you straight into your windows install.

why adding confusion with lilo ?

---

### Post by dino99 on 2010-05-04
> **Deuzy said:**
> I understand this however, I was unlucky enough to have a recovery partition instead. also, and I don't know if this would've worked or not, but i can't even get to the system recovery part of my computer. Grub takes over and doesn't let it execute.

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by oldfred on 2010-05-04
Leppie's post does not install lilo, but uses it to install a generic windows boot loader that works for windows. 

The windows boot loader in the MBR just looks for the active partition (boot flag) and jumps to the PBR of that partition. (That's all grub does when it chainboots windows - jumps to windows PBR)

---

### Post by Deuzy on 2010-05-04
thank you both leppie and oldfred.

I just want to confirm this.

I plan to remove my current kubuntu partition.
if i do the commands that leppie posted this will remove grub and i won't have any problems when I remove Kubuntu?

---

### Post by Leppie on 2010-05-04
that is correct, after having performed the operation with lilo, your bootloader should be set to factory defaults. this means, as oldfred already explained, that at boot the active partition will be checked for a boot loader.
lilo will in no way be installed on your system after you've removed the kubuntu partition(s).

---

