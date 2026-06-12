---
title: "Grub loader"
date: 2010-09-24
forum: General Help
---

### Post by Phil T on 2010-09-24
Hi Folks, 

First post so still finding my way around, apologies if this should have been posted elsewhere! 

Basic set up I have is 2 sata drives, 1st is a raptor which has win xp home installed, 2nd is/was a basic storage drive.

I managed to install ubuntu 9.10 on the 250 so had a dual boot with a grub loader that promted me to choose which OS to boot to.

I tried to upgrade/update 9.10 through a file manager of sorts (sorry can't remember exactly). Anyhow, it went wrong and I couldn't boot to ubuntu. 

So basically I managed to boot to win xp, no probs, but I decided to format the 250 to use as storage again. This was done in Windows disk manager. 

Now, when I try to boot I get a grub loading error along the lines of disk not found or does not exist. So I cannot get to select win xp anymore. I will want at some point to wipe the 250 of storage and get back to ubuntu and my learning curve of it!  

How do I get a grub loader to install so that I can boot again? 

Many thanks in advance

Phil T

---

### Post by btindie on 2010-09-24
When you formatted your 250 disk for use as storage under windows you would have deleted the files Grub uses in the boot process.
 
The easiest way to fix this is to use a windows recovery disk and use the fixmbr command.
 
I think previously Grub was the primary boot loader which would then load windows.
 
What happens if you go into your BIOS and change the boot order to boot off the other disk, does that make it work?

---

### Post by bilal_pieas on 2010-09-24
Hi there,

I think you just want to boot windows xp and not install grub because you already have uninstalled/deleted your ubuntu partition.

try booting from an xp cd and go to command prompt (via recovery console) then type "fixmbr". Reboot your system. Hopefully you will be able to boot xp.

---

