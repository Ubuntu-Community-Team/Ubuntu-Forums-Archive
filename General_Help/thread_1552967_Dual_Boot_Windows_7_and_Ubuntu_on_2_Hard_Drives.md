---
title: "Dual Boot Windows 7 and Ubuntu on 2 Hard Drives"
date: 2010-08-14
forum: General Help
---

### Post by garycheng12 on 2010-08-14
Before someone posts a guide to dual booting, this problem is different (or at least I think it is). What I am trying to do is: 

- Set up a menu (a boot loader?) to be able to select which OS,   
  Windows 7 or Ubuntu, to boot. 

The problem for me: 

- I have Windows 7 installed in an **internal** hard drive in the  
  computer. 
- I have Ubuntu 10.04 (32-bit) installed in a partition of an **external** hard drive.
 

What I currently am doing is: 

After installing Ubuntu on the external hard drive, I am able to run it without problems. If I were to unplug the external hard drive and restart the computer, the computer would boot into Windows 7 automatically, which is normal. If I plugged in the hard drive and then restarted the computer, it would automatically boot Ubuntu, which is what it should do. [B]However, how can I set up the boot loader such that I am able to SELECT which OS to boot if I had my external hard drive plugged in? It will boot into Windows 7 automatically if the user does not select an OS after 5 seconds. If external hard drive was not plugged in, then it will boot into Windows automatically. I don't know if GRUB has anything to do with this (I have never played with dual booting nor boot loaders before), then I prefer to use GRUB 2 as it seems to have significant advantages over the older version (I generally prefer using up-to-date applications as they almost always contain speed/security improvements). 
[/B]

I know that Startup Manager can tweak the GRUB and customize it to my likings, but how can I actually setup GRUB to perform the task above?

Thanks, guys.

---

