---
title: "vmlinuz and initrd.img broken"
date: 2012-02-04
forum: General Help
---

### Post by kibbles2 on 2012-02-04
Can someone please assist a newbie please. I am running v9.04 only and this morning I started getting this error message.
 
Boot from CD:
 
PXE-E53: No Boot File Name Received
 
PXE-M0F: Exiting NVIDIA Boot agent
 
Disk boot failure, insert system disk...
 
I can boot from live CD.
 
I know how to get to the terminal, sudo or grub.
 
Once I boot from live CD, I can go into the file system and see that root, vmlinuz and initrd.img are broken (red box with X) 
 
Can someone please guide me in on how I can recover my master boot record (MBR). I do not know what "mount" means and I do not know how to partition.
 
Also, if I do an "install" or upgrade to: EX 10.04, will I lose my files? I have many of my most favored files backed up to an external drive but I don't know how to save the "master file" of all my emails, like I do in windows.
 
I have video so my INVIDIA card must be working. What the heck happened?
 
How can I save my MBR so the next time this happens I don't have to spend all day Saturday trying to get my computer back up? 
 
With all this trouble, any bad Ubuntu day is better than the best WinTel day!
 
RH:confused:

---

### Post by dcstar on 2012-02-04
> **kibbles2 said:**
> Can someone please assist a newbie please. I am running v9.04 only and this morning I started getting this error message.
 
Boot from CD:
 
PXE-E53: No Boot File Name Received
 
PXE-M0F: Exiting NVIDIA Boot agent
 
**Disk boot failure, insert system disk...**
......

Your hard drive is dead or totally corrupted.

---

### Post by lolpenguin on 2012-02-05
> **kibbles2 said:**
> Can someone please assist a newbie please. I am running v9.04 only and this morning I started getting this error message.
 
_**Boot from CD:**_
 
PXE-E53: No Boot File Name Received
 
PXE-M0F: Exiting NVIDIA Boot agent
 
Disk boot failure, insert system disk...
 
I can boot from live CD.
 
I know how to get to the terminal, sudo or grub.
 
Once I boot from live CD, I can go into the file system and see that root, vmlinuz and initrd.img are broken (red box with X) 
 
Can someone please guide me in on how I can recover my master boot record (MBR). I do not know what "mount" means and I do not know how to partition.
 
Also, if I do an "install" or upgrade to: EX 10.04, will I lose my files? I have many of my most favored files backed up to an external drive but I don't know how to save the "master file" of all my emails, like I do in windows.
 
I have video so my INVIDIA card must be working. What the heck happened?
 
How can I save my MBR so the next time this happens I don't have to spend all day Saturday trying to get my computer back up? 
 
With all this trouble, any bad Ubuntu day is better than the best WinTel day!
 
RH:confused:
What?? It looks like you are trying too boot from a CD when there is none in the drive. Change the boot sequence in the BIOS (refer to your motherboard's manual).

---

### Post by xyzzyman on 2012-02-05
No, his HDD isn't being read for boot so it's defaulting to trying to PXE boot (Off his ethernet jack, he most likely has an nforce controller on his mobo) but there is no PXE server on his network. So as it doesn't detect a HDD or PXE server for ethernet, that's the expected error. This has nothing to do with his BIOS settings unless he disabled his IDE or SATA controller, and it definitely has nothing to do with changing his boot order.

---

### Post by kibbles2 on 2012-02-05
In my BIOS settings, I have the HDD list as both 1st and second choice.  Third choice is the CD.  
 
Since the HD is not seen, it defaults to the CD:  I just don't know how to get the HDD to boot.  It runs fine, though it seemed to be a bit slow the last time I used it.

---

### Post by kibbles2 on 2012-02-05
First, if I do a reintall, do I lose all my files?
 
Second, how can I check the system to ensure my HDD, Video card, network card are working properly?  Device manager in Windows equivalent?

---

### Post by xyzzyman on 2012-02-05
You need to backup your data immediately if you can access it. Everything points to drive failure.

---

