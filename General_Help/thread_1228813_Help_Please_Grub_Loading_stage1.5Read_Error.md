---
title: "Help Please Grub Loading stage1.5Read Error"
date: 2009-08-01
forum: General Help
---

### Post by Ultravires on 2009-08-01
Hi guys, i am totally new to linux here. I just tried installing ubuntu 9.0.4 and came across this error GRUB Loading stage1.5Read Error any idea on what is causing this or how i can easily fix it?
 
Here is some info, i have a ASUS P5PE-VM motherboard and i am able to detect the Western Digital harddrive in the bios section. I tried to instal ubunto onto the hardrive and i gave the entire drive to ubuntu. Before i had a working windows o.s on it. 
 
Please provide some information on how to solve this problem. TIA

---

### Post by Brandon Williams on 2009-08-02
I suggest that you boot the computer from a live CD and reinstall grub to the MBR. [Here](http://ubuntuforums.org/showthread.php?t=224351) is a forum thread that should help.

---

### Post by gryptix on 2009-11-29
Hi all,

I would recommend to disable the "IDE Bus Master Support" in BIOS.

I had this problem recently again, although already fixed last year. I have an older Suse installation, but for some reasons, the BIOS had been reset to defaults. 

Hope this helps.

Gerhard

---

