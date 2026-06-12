---
title: "How to install grub from Live CD?"
date: 2011-05-24
forum: General Help
---

### Post by searchfgold6789 on 2011-05-24
Hello,
I just need help with a problem in Grub, here it is: I tried installing grub from the Live CD to one of my hard disks (/dev/sdc) on a PCI to ATA adapter. I wanted to be able to choose which OS to boot from when the ATA adapter booted from the hard disk with GRUB on it, but all I get is a GRUB prompt. How do I make a normal GRUB menu on that hard disk with all my OS'es on the menu??
Any help would be much appreciated.
 - search
P.S. Boot Info Script results attached for clarification.

---

### Post by seawolf167 on 2011-05-24
Take a look at the [instructions here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). After you get GRUB reinstalled and booted into your OS, run 

```
sudo update-grub
```

to use the os-proper and search for other OS's.

---

### Post by searchfgold6789 on 2011-05-24
I cannot boot into my OS, all I see is a black screen and a message, with a grub> prompt. Is there a way to get into my OS and then update-grub?
Currently, I booting onto the hard disk which had no OS on it, /dev/sdc. It has grub but no menu.

---

### Post by seawolf167 on 2011-05-24
You should get the menu after a reinstall of GRUB, but it sounds like you are entering the GRUB rescue prompt.

Take a look [here ]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")for command line options. Specifically, you'll want to read the section "Boot a Specific Kernel Manually" & the "Rescue Mode", where you can manually boot your partition. 

An example would be;

find the partition table geometry 

```
geometry (hd0)
```where hd0 is your disk

```
root (hd0,4)
```where hd0 is your disk, and '4' is the partition number with your boot files

```
setup (hd0)
```to setup GRUB for hdd hd0

---

### Post by searchfgold6789 on 2011-05-25
Before I read that helpful post of yours, I removed excess hard disks and now there are only two partitions I care about that are remaining; /dev/sda1 (windows) and /dev/sdb1 (linux). Unfortunately only the Windows partition is recognized by the GRUB CLI, and I am assuming this means I can't boot anything on my Linux drive.
What do I do now???

---

### Post by seawolf167 on 2011-05-25
> **searchfgold6789 said:**
> Before I read that helpful post of yours, I removed excess hard disks and now there are only two partitions I care about that are remaining; /dev/sda1 (windows) and /dev/sdb1 (linux). Unfortunately only the Windows partition is recognized by the GRUB CLI, and I am assuming this means I can't boot anything on my Linux drive.
What do I do now???

Follow [this guide ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")first to reinstall GRUB and point to your correct Ubuntu installation. After you get GRUB reinstalled, boot into Ubuntu, open a terminal and type

```
sudo update-grub
```

then restart and you should see your Windows boot loader entry

---

### Post by searchfgold6789 on 2011-05-25
Still same results; no menu just a grub> prompt. 'ls' does not recognize (hd1,0) which is my linux partition.

---

