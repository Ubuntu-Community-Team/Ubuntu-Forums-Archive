---
title: "Booting Issues w/ Windows 7"
date: 2010-03-16
forum: General Help
---

### Post by shibby4555 on 2010-03-16
So I used a live cd to install Ubuntu onto my new Toshiba laptop a couple weeks ago, installation went fine and then destroyed my computer where it would only reach the BIOS menu before shutting down.

Now I have an HP Pavilion dv6 notebook where I installed Ubuntu right from my desktop, everything went well until I actually try to boot Ubuntu where I get a screen that says "Completing Installation" and then a black screen, my keyboard and mouse are all unresponsive and I have to power off. 

Can anybody help me out here and explain in the most simplistic terms possible, (I am not very computer savvy). I've been browsing around and apparently it can be related to an issue with Windows 7 not being able to run other OS or something? I'm going nuts here! 
Thanks!

---

### Post by oj0kksn5 on 2010-03-16
are you trying to dual boot (two operating systems) or you just installing ubuntu instead of windows?

what version of ubuntu are you installing?

P.S. just thought can you check in the bios to see if you can find what sata mode you are running in? if you can find it post what the option is which im guessing it will be ahci if so try changing it to the other option normally is IDE

---

### Post by shibby4555 on 2010-03-16
Yes I'm dual booting, both the Windows and Ubuntu OS show up on startup at this point. I installed 9.10 version. As for the sata mode, I believe Windows 7 default is ahci but I ran thru the bios page and can't figure out how to change it

---

### Post by prodigy_ on 2010-03-16
> **shibby4555 said:**
> So I used a live cd to install Ubuntu onto my new Toshiba laptop
Can be tricky because Toshiba hardware isn't known for its great Linux support. What error message it gives you when you try to boot it?

Did you use Wubi? I'd advise against that. Wubi makes it harder to troubleshoot dual-boot issues and is more prone to breaking down after kernel updates. Anyway, I suggest you to go step-by-step. First, restore untampered Windows bootloader (there's a recent [thread](http://ubuntuforums.org/showpost.php?p=8974780&postcount=2) with HOWTOs) and make sure you can boot into Win7. Then you can reinstall Ubuntu from Live CD. Just be careful with partitioning.

---

### Post by shibby4555 on 2010-03-16
The first time I tried Ubuntu was from a live cd with a brand new Toshiba. First I tried the demo version and it gave me the black screen, then when I actually installed it, it wouldn't even boot Windows so I exchanged my laptop for an HP, I tried the live cd again in demo mode and immediately got the black screen, and learning from my mistake with my Toshiba, I thought it'd be foolish to try the full installation. 

And yes I used Wubi.

---

### Post by prodigy_ on 2010-03-16
You shouldn't be scared of black screens. Boot issues are not uncommon, but as long as your Windows partition is intact, you can simply restore Win7 bootloader (just boot from Win7 installation DVD and follow instructions from the HOWTOs I posted earlier).

Now, if you want a dual boot system, the best is to go back to square one (remove Wubi) and then carefully install Ubuntu from Live CD.

---

### Post by shibby4555 on 2010-03-16
Well the thing is, when I installed the Live CD onto my Toshiba, I wasn't even able to access my bios page, so I don't think a recovery disc would have even helped. But I'm creating some recovery files

> Now, if you want a dual boot system, the best is to go back to square  one (remove Wubi) and then carefully install Ubuntu from Live CD.     When you say carefully install the Live CD, is there anything differently that I should do?
And I'm assuming I should install 64 bit?
Thanks so much for your help guys.

---

### Post by Mark Phelps on 2010-03-16
> **shibby4555 said:**
> When you say carefully install the Live CD, is there anything differently that I should do?

Yeah ... don't use the Ubuntu installer to shrink your Win7 OS volume to make room for Ubuntu.  Doing so risks corrupting the Win7 OS volume and rendering it unbootable.  Use the builtin Win7 Disk Management utility to shrink the OS.  Don't format the newly unallocated space in Win7.

Use the Ubuntu installer to select the free space and allow it do to the formatting.

---

