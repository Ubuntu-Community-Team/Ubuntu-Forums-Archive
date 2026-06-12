---
title: "Latest Kernels not visible in Grub2 boot menu"
date: 2011-09-28
forum: General Help
---

### Post by jaredscribe on 2011-09-28
[http://ubuntuforums.org/showthread.php?t=1851277](http://ubuntuforums.org/showthread.php?t=1851277)

I have several kernels on my filesystem in the /boot directory:
 initrd.img-2.6.38-11-generic
 initrd.img-2.6.38-10-generic
 initrd.img-2.6.38-8-generic

 However, only 2.6.38-8-generic appears in the boot menu, (in both regular and recovery mode).  Another kernel is listed that is on a different partition, which I use to boot a different Ubuntu version on, but that shouldn't matter.

 As I understand, Grub2 is smart in that it looks in the /boot directory for kernels and does some magic to auto-populate the boot menu.  So it should detect it.  Also, I inspected the /boot/grub/grub.cfg and it has menu entries for all 3 of these kernel versions! So why is only 2.6.38-8 displaying?

Also, each kernel version has some other files associated with the version number, vmlinuz-x.x.xx-xx, System.map-x.x.xx-xx, etc.  What do these do, by the way?

---

### Post by jaredscribe on 2011-09-28
I was booting into /dev/sda1 (my primary installation, Natty) from a version of Grub2 installed on a secondary Lucid Lynx installation on /dev/sda3.  

The new task is to edit the MBR to point to the bootloader in /dev/sda1 where Natty is installed, along with all the recent kernels.

Now I'm going to spend some quality time alone with the gnu grub manual and figure out how to resolve this and maybe get to know how this thing works.  Any instructive comments are welcome.

---

### Post by garvinrick4 on 2011-09-28
If you are using one install as control of grub and upgrade the kernel on another install unless you:
```
sudo update-grub
```You are not going to make a new grub config file so as to put the new kernels for the
other install or installs as menuentrys and as part of that installs config file.

##The part of grub2 when grub updated that go's out and looks for other operating systems and their kernels is "os-prober"
Package: os-prober                       
State: installed
Automatically installed: yes
Version: 1.49ubuntu1
Priority: optional
Section: utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 197 k
Depends: libc6 (>= 2.4)
Description: utility to detect other OSes on a set of drives
 This package detects other OSes available on a system and outputs the results
 in a generic machine-readable format
## If you want to watch the config file being made:
```
sudo grub-mkconfig
```Look for when this begins and you will see other installs and their kernels--  /etc/grub.d/30_os-prober

---

### Post by jaredscribe on 2011-10-01
Thanks garvinrick.  I was able to refresh the grub.cfg using grub-mkconfig.  I also used grub-rescue to make a bootable grub2 rescue CD.  

After booting from the grub rescue CD into my main OS on /dev/sda1, grub-update updated my MBR's bootloader to the latest config and grub2 version on the correct partition (/dev/sda1).  I did that because the grub2 manual advised against running grub-update on a running OS.

---

### Post by jaredscribe on 2011-10-01
Thanks garvinrick.  I was able to refresh the grub.cfg using grub-mkconfig.  I also used grub-rescue to make a bootable grub2 rescue CD.  

After booting from the grub rescue CD into my main OS on /dev/sda1, grub-update updated my MBR's bootloader to the latest config and grub2 version on the correct partition (/dev/sda1).  I did that because the grub2 manual advised against running grub-update on a running OS.

---

### Post by jaredscribe on 2011-10-01
Now, when I boot from the HDD, I come to the grub2 prompt, for version 1.99.
I understand there's a commandline syntax for interactively setting options and booting, but how do I set up a menu page to load by default rather than the interactive prompt?

---

### Post by garvinrick4 on 2011-10-01
> I understand there's a commandline syntax for interactively setting  options and booting, but how do I set up a menu page to load by default  rather than the interactive prompt?
 Yes there is will give you.
Need to see your 
```
sudo fdisk -l
```lower case L

Post results please.

---

### Post by garvinrick4 on 2011-10-01
> As I understand, Grub2 is smart in that it looks in the /boot directory  for kernels and does some magic to auto-populate the boot menu.  So it  should detect it.  Also, I inspected the /boot/grub/grub.cfg and it has  menu entries for all 3 of these kernel versions! So why is only 2.6.38-8  displaying?


As for links about grub2 and the new sub directorys (your other kernels) and all
things grub I myself use tutorials by drs305. He has a list of tutorials in this link below.
: Do read on the sub-directorys though.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)

---

### Post by drs305 on 2011-10-01
I you run the boot info script it will tell us a lot about the status of your boot files (it includes fdisk results). You can get the script by clicking the "BIS" link in my signature line.

Once you run the script (from a running Linux OS or the LiveCD), please post the contents of RESULTS.txt. Perhaps we'll be able to see why your system isn't posting everything.

---

### Post by garvinrick4 on 2011-10-01
> Perhaps we'll be able to see why your system isn't posting everything.He has 2 installs of Ubuntu I just believe OP has not updated grub that is in control of
grub as to make a new config file with new kernels. Not booting either now. Boot script will tell whole story, if OP will run, better than my guess.

---

### Post by drs305 on 2011-10-01
> **garvinrick4 said:**
> He has 2 installs of Ubuntu I just believe OP has not updated grub that is in control of
grub as to make a new config file with new kernels.

I would guess you are correct. The 'controlling Grub' issue is something that even experienced users have to monitor. 

I make sure my menus are either color-coded or embed a title so I can tell at a glance which system's Grub I'm looking at. Without modification or added scripts, the controlling Grub can be determined by checking which OS or kernel is listed first in the menu.

RESULTS.txt should show us the controlling partition and why nothing is currently booting.

---

### Post by jaredscribe on 2011-10-14
Hi garvinrick and drs305, thanks for the help.
When I last wrote, I was encountering a grub2 prompt, but not getting the menu.  Still not sure why, but its a moot point now.

I installed another distro on another partition (which I had to do anyway for a separate task), which installed its own bootloader.  Using that I could boot to any partition.  I booted into Ubuntu on /dev/sda1 and ran grub-install with an argument instructing it to load from the grub2 on /dev/sda1.  When that was done I had the right version, from the right system, and with a nice boot menu defaulting to Ubuntu.

---

