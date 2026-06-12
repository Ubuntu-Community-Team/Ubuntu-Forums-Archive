---
title: "Partition Delete"
date: 2011-09-09
forum: General Help
---

### Post by azazi on 2011-09-09
Hello,

I am running 11.4 natty with dual boot. I need to re-install, and I wanted to clarify if I go under windows and delete sda4 and sda5 where Ubuntu is partitioned, will my computer still boot? I wanted to confirm that this action wont destroy my computers BIOS and leave me with an expensive rock....

EDIT: There was technically no solution. I got angry, stepped away from my computer, then my girlfriend walked over and pressed the power button and it came right up.....7 hours of work and it just decides to come up. Life is weird.

---

### Post by YesWeCan on 2011-09-09
I don't think you'll have an expensive rock, but it wont boot. :P

If your dual boot is on the same disk and you boot using Grub then deleting the Ubuntu root partition will break Grub. The remedy is to boot into Ubuntu and restore the standard MBR boot code first.

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Also just check using sudo fdisk -lu that the boot flag is set on the Windows boot partition.

Then reboot and it should go straight into Windows. Then it is safe to delete the Ubuntu partitions.

---

### Post by azazi on 2011-09-09
Yea, the problem is that my Ubuntu will NOT work....idk what happened but the live CD won't even boot anymore. I want to start over!

---

### Post by YesWeCan on 2011-09-09
You'll need a Ubuntu CD or USB to reinstall Ubuntu tho.
Have you got a Windows installation CD? You should be able to do a repair of the MBR.

---

### Post by fdrake on 2011-09-09
> **azazi said:**
> Yea, the problem is that my Ubuntu will NOT work....idk what happened but the live CD won't even boot anymore. I want to start over!

ehhmmm... live cd not working?
check your Bios setting and select boot from cd-rom.
 Can you boot into the windows partition? if so you can try to make a new live-cd or use the existing one to install temporarily  wubi, just to run those commands.

---

### Post by azazi on 2011-09-09
To summarize, I am on that computer under windows right now. I made an iso file on a USB and CD, the same CD I used to install Ubuntu on a few months ago. They both load, but when they get to the screen where you would normally log in, it turns black and fails. I cant get GRUB to load (The shift thing), and when i boot under safe mode, it has a "fatal error" and reboots...... Everything was working fine until 4 days ago.

---

### Post by fdrake on 2011-09-09
> **azazi said:**
> when i boot under safe mode, it has a "fatal error" and reboots...... Everything was working fine until 4 days ago.

keep shift pressed until you see the grub menu. then press "shift" again to go to the recovery menu. from there select "root" from the menu. can you run
```
fdisk -lu
```
copy here the output.

also what exactly is the error about ? did you change/edit the partitions before? run also a
```

fsck -y -t ext3

```
and see if that solves the problem.

---

### Post by aeathb on 2011-09-10
`

---

### Post by azazi on 2011-09-10
Okay, So last night I tried booting to get the grub menu and nothing new comes up..... I tried searching for that issue and I can't figure out what exactly I need to do. If the live CD ran that would be awesome.....but it doesn't.
EDIT: and I certainly booted off the CD and USB. it comes up and I try to boot off of the live CD/USB, and it crashes in the same place as booting off the hard disk....

---

### Post by azazi on 2011-09-11
So basically how do I delete Ubuntu if I cant get into it or boot off of a live CD? I'm lost and I'm worried and don't know how to fix this!

---

### Post by fdrake on 2011-09-11
how did u solve the problem? were u able to boot from the cd?

---

