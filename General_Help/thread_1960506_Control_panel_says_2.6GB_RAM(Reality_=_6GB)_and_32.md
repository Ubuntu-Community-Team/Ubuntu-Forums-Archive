---
title: "Control panel says 2.6GB RAM(Reality = 6GB) and 32BIT OS"
date: 2012-04-17
forum: General Help
---

### Post by Jaxke on 2012-04-17
Hi.

Today I got a weird problem. When I go to Computer Info in System Settings, it says that I have only 2.6GB of RAM and a 32bit version of Ubuntu. 
My laptop has 6GB of RAM and I'm sure I run 64bit Ubuntu. It never told me so before(a week ago I checked, and it was 6GB and 64bit)

And it's not that only, I've witnessed some serious lagging, especially in Firefox. Also programs take a lot of time to start.

Why? What happened? Maybe because of my new Cairo-Dock desk environment(When I went to Gnome Classic, it also had false specs!)?

Thanks for help! I hope there's another solution than reinstall, I have nowhere to backup my data...

---

### Post by oldfred on 2012-04-17
Post this:

32 or 64 bit
```
uname -a
```
i386 or i686 = 32-bit
x86_64 = 64-bit

Have you run a memory test from the grub menu. What does BIOS say about memory. It should show the 6GB.

You should really have backups of at least your most important data.

---

### Post by efflandt on 2012-04-18
With that much RAM you should really be running 64-bit Ubuntu.

32-bit is limited to about 3 GB max unless you install a **pae:i386** kernal.  I am not sure how that works around 32-bit not having enough digits to access more RAM.  But unless you have some program that is only available in 32-bit, I would suggest running 64-bit.  And there are libs you can install to run 32-bit apps on a 64-bit system.

---

### Post by HiImTye on 2012-04-18
if you are using 32bit Linux you will need to switch to a 32bit PAE kernel, or you will be limited to 4GB total memory address space (meaning all of the memory on any chip or card, combined, will be limited to 4GB total)

---

### Post by mastablasta on 2012-04-18
it owuld be good if someone read before they posted. 
 
the OP says they had 64bit system before and after installing a few things the system is showing to be 32 bit and full ram is not displayed.

---

### Post by HiImTye on 2012-04-18
> **mastablasta said:**
> it owuld be good if someone read before they posted. 
 
the OP says they had 64bit system before and after installing a few things the system is showing to be 32 bit and full ram is not displayed.
in which case, my instructions will work
it's likely that by '64 bit system' he means '64 bit processor' and not '64 bit operating system'

---

