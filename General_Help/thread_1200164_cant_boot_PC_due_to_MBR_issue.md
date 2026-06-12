---
title: "cant boot PC due to MBR issue"
date: 2009-06-29
forum: General Help
---

### Post by richardy on 2009-06-29
Hi,
I have a problem booting my laptop. I currently have xubuntu 8.10 dual booted with windows XP i then decided to try xubuntu 9.04 by putting it on to a USB flash drive using the setup file xu904p.exe and the iso file for xubuntu 9.04. Everything seemed to go fine except when i went to reboot i got a blank screen nad that was it. I assume the MBR has been overwritten/corupted. I can boot into windows if i use Gparted and select the 'boot from 1st partition' option of Gparted but cant seem to boot into Xubuntu using any of the other options. 

If i try to boot (using Gparted) using the 'Boot MBR on first hard drive' option i get teh following:

rootnoverify (HD0)
chainloader +1

Then nothing happens. I assume there must be a command that i can use under Gparted to boot xubuntu. However i still have teh problem of how to fix the MBR to dual boot the two systems again.

I had this problem once in the past and got around it buy reinstalling linux as this writes a new MBR but not to keen to do this. Another option would be just to upgrade to Xubuntu 9.04 but do i need ot get access to old system to do this or could i do it from a live CD.

Any help would be much apreciated as i mostly use Xubuntu now.

Cheers.

---

### Post by richardy on 2009-06-30
Anybody??

---

### Post by louieb on 2009-06-30
Just a guess that code in the MBR is is trying to load grub on the pen drive.

The fix is same as if you had installed windows after Linux - replace the code in the MBR with code that loads grub located on the hard drive. 

[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

probably an easier way is to use a [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") to fix

---

