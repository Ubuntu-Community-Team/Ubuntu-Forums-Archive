---
title: "Dual Boot - What if I wipe the Windows Drive Clean?"
date: 2010-10-27
forum: General Help
---

### Post by gwm on 2010-10-27
Hi,
Can anyone tell me where to find the answer?
I have two hard drives - one for XP and one for Ubuntu 10.4. As far as I know, this means that I first boot to the XP drive, which redirects me to the Ubuntu drive and Grub 2.
I want to wipe the XP drive by installing Ubuntu 10.10 over the top of it.

Question:
Is there a way of setting the boot process to run off the Ubuntu drive only, so that I can wipe the other one?

Oh, I forgot to mention the hardware. That would affect the boot options.
I have a fairly new 64 bit core duo motherboard.

---

### Post by sikander3786 on 2010-10-27
Are you sure Grub is installed to the MBR of your Windows drive? If yes, you can format your Windows drive and reinstall Grub to the Ubuntu drive as mentioned here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If it is already on the Ubuntu drive, you just need to format the Windows drive and run

```
sudo update-grub
``` afterwards.

---

### Post by Quackers on 2010-10-27
Are you getting a grub menu on boot up?

---

### Post by gwm on 2010-10-28
Thanks for the input.

I have been reading the page in the suggested link and learning by deduction.

I think we aren't on the same page. I have a working system with two hard drives. I installed XP on one hard drive and then I installed Ubuntu 10.4 on the other drive in a dual boot configuration. It is all working just fine but I am about to change all of that.

I want to boot straight into Ubuntu and run Windows in a virtual machine. That way I can have access to Windows programs that I haven't ever managed to get up and running in Wine (Ones that access Sql and Access databases)

To that end, I want to wipe the windows hard drive and install Ubuntu 10.10 on it. Before I do that though, I want to cover my bases and be sure that the drive with 10.4 can still be booted after I have wiped the Windows drive. I may need that when it comes to transferring my Evolution files or whatever. What if I duffed up and need to go back and export them again or something. 

Thanks again for the link you gave me, I have played with Disk Utility and have found that it lets me mark the drive as bootable. So I can get to boot to the Ubuntu Drive. But ...

How does the BIOS find Grub2 and hand over control to it?
Is the needed linkage already in the MBR of the said drive?
Will I perhaps have to reinstall Grub2 as described to create the link?
Am I stressing for nothing?

---

### Post by wilee-nilee on 2010-10-28
Lets have a better look at the whole setup, post the bootscript in my signature in code tags as described in my signature. Or generate the code tags by clicking on the (#) in the reply panel and put the text in between. 

Removing XP could be done from a live Ubuntu, but it is better to use a live cd. I want to know more before about your setup before confirming any of this though.

---

### Post by 73ckn797 on 2010-10-28
You can boot from the 10.10 CD and install it. When you get to the part of choosing which drive select the manual setup and mark the Windows drive as the Ubuntu drive and mark it for formatting. You can also create separate "/" and "/home" partitions at that time.

---

### Post by Mark Phelps on 2010-10-28
Don't do ANYTHING until you run the script that wilee-nilee suggested.

We want to be sure that Ubuntu is entirely contained on the second drive -- NOT a Wubi installation that is merely hosted on the second drive.

If the first is true, wiping XP will not harm Ubuntu; but if the second is true, wiping XP will wipe out Ubuntu.

---

### Post by gwm on 2010-10-29
Thanx guys,
There is no WUBI! I did say: "dual boot", "Grub2" etc.
This is now how I understand things. I hope it is right. At any rate, this model seems to describe what is on my PC.

After the XP install, the Ubuntu installation modifies the Windows MBR to point to the Ubuntu partition. In this case, the partition is on another disc, so the MBR is modified to activate the correct drive, load it's MBR code and execute it.

To resolve my problem, I simply performed that action manually. I used "Disk Utility" to set the Ubuntu drive as bootable and likewise to turn off the bootable flag on the windows hard drive. (I figured I could reverse that using the Live Cd if necessary.) My BIOS found the second drive and booted from it quite happily.

This worked just fine, so I went ahead and zapped the Windows drive. Still no problem, so when I get some more time, it's on with the show!

Thanks again for your help.

---

### Post by wilee-nilee on 2010-10-29
Glad you got it the way you wanted, actually Ubuntu doesn't have to have a boot flag.

You have to remember that when we help people on line even if you say dual boot and grub I want the proof before I will advise. Those words alone don't really confirm enough for me.

---

### Post by Mark Phelps on 2010-10-29
> **gwm said:**
> Thanx guys,
There is no WUBI! I did say: "dual boot", "Grub2" etc.


If I got $5 for every time someone said dual-boot here, or side-by-side here, and they actually had WUBI, I could have retired by now :)

We try to follow the practice around here of "better safe than sorry".  That's why we ask for confirmation before making recommendations that could possibly wipe out a full installation.

---

