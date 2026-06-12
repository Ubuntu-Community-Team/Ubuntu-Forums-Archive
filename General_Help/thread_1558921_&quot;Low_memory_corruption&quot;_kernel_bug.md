---
title: "&quot;Low memory corruption&quot; kernel bug"
date: 2010-08-22
forum: General Help
---

### Post by Chris1274 on 2010-08-22
I think I may have come across a solution (or at least a band-aid) for a bothersome bug. When I open up a tty terminal I'm greeted by a "Corruption in low memory" message. I've done a memtest and know that there's nothing wrong with the memory, so it's a false flag caused by a bug in the kernel. Searching for answers, I came across this message in the Arch Linux forum:
>  						Fancy thing this "Corrupted Low Memory", as I get it as well on my T42...
I  downgraded to kernel 2.6.30.1 and still had the Corrupt message in my  dmesg.  I then downgraded to 2.6.29.1 and voila the Corrupt messages  went away, and so did the random module crashes (as you seem to be  getting too after the Corrupt messages).  
The problem seems to be with:
CONFIG_X86_CHECK_BIOS_CORRUPTION: Check for low memory corruption
Which  is a new feature ever since 2.6.28.x kernel.  It was working properly  for us T42 ppl, until 2.6.30.x came along, and still hasn't been fixed  in 2.6.31.x.   To fix this and get system stability back, add the  following to the end of your kernel line (in either Lilo or Grub):
memory_corruption_check=0
That  stops the kernel from checking for corrupted low memory, but, since the  check procedure messes up the system and causes modules to crash, it's  better to disable it until the problem is worked out.
To be on the  safe side, I ran a few memory check programs, and they all ran without  errors.  So my low memory isn't corrupt after all, just a bug in a  feature that can be disabled.


Now, can someone explain to me what he means by the "kernel line"? I'm not sure what file I need to edit here in order to disable the memory corruption check. My guess would be /etc/default/grub, but before I bork my system I thought I'd ask for some advice here first. Thanks in advance.

---

### Post by happyhamster on 2010-08-22
> **Chris1274 said:**
> I think I may have come across a solution (or at least a band-aid) for a bothersome bug. When I open up a tty terminal I'm greeted by a "Corruption in low memory" message. I've done a memtest and know that there's nothing wrong with the memory, so it's a false flag caused by a bug in the kernel.
That message has nothing to do with the hardware side of RAM, it means some piece of software is incorrectly writing into RAM (with the chance of stuff breaking later). Corruption of low memory is usually caused by the BIOS. 

> 
Now, can someone explain to me what he means by the "kernel line"? I'm not sure what file I need to edit here in order to disable the memory corruption check. My guess would be /etc/default/grub, but before I bork my system I thought I'd ask for some advice here first. Thanks in advance.
Well, first of all, if you're only seeing that message, and there aren't any other problems, then everything's well. For example, see:
[http://cateee.net/lkddb/web-lkddb/X86_CHECK_BIOS_CORRUPTION.html](http://cateee.net/lkddb/web-lkddb/X86_CHECK_BIOS_CORRUPTION.html)
[http://kerneltrap.org/mailarchive/git-commits-head/2008/10/12/3624954](http://kerneltrap.org/mailarchive/git-commits-head/2008/10/12/3624954)

Disabling the check will only *cause* problems in that case.

Anyway, if you want to disable it; you're correct, it can be set in /etc/default/grub. That file should have a line similar to :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change that into:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash memory_corruption_check=0"
```
Save the file, then update grub:
```
sudo update-grub
```
Then do a reboot to see if it works. Good luck.

---

### Post by Chris1274 on 2010-08-22
Hmm, maybe a BIOS update would be a better fix. The only problem is that I have no idea how to do that.

Edit: Looks like I've got the latest BIOS version, so no update possible anyway

---

### Post by Chris1274 on 2010-08-24
I checked the x86/Kconfig file in the kernal and it's set by default to reserve the low 64K ram. Since that's the only area that the check is finding corrupt, I'm going to try disabling the check and see what happens.

Crossing my fingers and holding my breath ...

---

