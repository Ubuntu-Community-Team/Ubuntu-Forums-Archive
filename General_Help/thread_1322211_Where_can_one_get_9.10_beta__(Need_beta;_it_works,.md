---
title: "Where can one get 9.10 beta ?? (Need beta; it works, official release does not)"
date: 2009-11-10
forum: General Help
---

### Post by buntuyu on 2009-11-10
I can no longer find the beta 9.10 Ubuntu 

Due to some crazy, improbable glitch, unlike the beta version, the official 9.10 release installs on the Motion Computing M1400 but fails to boot, and no grub menu to pass kernel options.

(The 9.10 beta works for the M1400 with the "acpi=force" option)

I lost my beta CD; Please help me locate it for download again!

thanks.

---

### Post by wojox on 2009-11-10
Why don't you just install 9.10 Final with the "acpi=force" option

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
Do you need the 32 or 64 bit edition?

---

### Post by buntuyu on 2009-11-11
To wojox: I did install the final release, using "acpi=force", at the beginning of the install, pressing F6 to get the option list with that option.

I did not see anywhere DURING the install, a place to add the "acpi=force" PERMANENTLY to grub.

Thus, on FIRST (re)BOOT, after the install, the option (i presume) was NOT there.

And grub immediately goes non-interactive, ending in a blinking cursor and  a non-responsive state (hangs forever).  I can't interrupt it to add the "acpi=force" option.

Thus, the system never boots after the install (which itself has no errors).  (Although the reason it does not boot might be different from the known acpi problem with this tablet pc (with particular BIOS versions))

To ST3ALTHPSYCH0: It's a 32-bit tablet PC

---------

Again, I was able to overcome the ACPI problem with the beta version (by entering the grub menu, post-install).

By the way, I have since reobtained the iso file I had downloaded (was geographically far away); its md5sum is c07bc8085ab72e25b9372db4a2f6f784 

I hope that's correct.

Thanks for the replies

---

### Post by louieb on 2009-11-11
Seems to me that you could use a live CD and modify /boot/grub/grub.conf to add "acpi=force". 

At least you can see if will boot. Then you'll have to figure out how to get GRUB2 to make it permanent.  Not much help there - still trying to figure out GRUB2 myself.

---

### Post by ST3ALTHPSYCH0 on 2009-11-11
That's a shame... I have a 9.10 64 bit beta that I could .iso (if I don't still have the original .iso), but obviously that won't help.
[This link](http://isohunt.com/torrent_details/134204969/Ubuntu+9.10+beta?tab=summary) claims to be the beta, but I can't verify that anyone is seeding.

---

### Post by falconindy on 2009-11-11
Holding down shift takes you into Grub2's menu, much like hitting escape did for Grub-legacy.

---

### Post by pookiebear on 2009-11-11
use the 8.04 LTS to live boot and edit the grub?
OR puppylinux (100mb)
or slitaz (30mb live) 

at least try those to edit grub. until you can get a beta copy from somewhere.

---

### Post by wilee-nilee on 2009-11-12
I have a daily release from about a week ago the up to date version it installs with grub legacy rather then grub2. It installs grub2 in the updates you might see if the latest daily on a live CD is legacy so that you can adjust the acpi before you upgrade and keep the old grub menu when asked during updating.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I suspect the daily builders are aware of the grub2 problems I have had none, but some people do and it is a hack edit to change the grub2 menu.

---

### Post by buntuyu on 2009-11-12
Thanks for so many helpful replies.

I hope what I'm about to say does not induce (too much) wrath, however:

(Also, I'll TRY to make this as short as possible, but that's a challenge)

I reinstalled the Beta (I *did* post an update here saying I found my iso). Initially I got the blinking cursor upon reboot (couldn't interrupt grub still). This was a great surprise (as I claimed earlier that the beta worked for me), and it drove me to keep trying to get into grub, because I remember having a (quasi-)working system with the beta a couple of weeks ago.

So, I was finally able to get into grub menu by hitting "F1". (I had tried the shift key before but apparently did not hold it down, as falconindy suggested.)

IN ADDITION: I messed up here by misremembering the kernel option; apparently "acpi=force" does NOT work for this tablet, but "acpi=off" does.  (I come from years of Fedora & grub 1) 
I thought I replaced "off" in "acpi=off" with "force" and that made the "shutdown" and "hibernate" options appear in the upper right menu, but I am somewhat confused at this point (these options do appear now, with "acpi=off"; i could have sworn they were missing at some point before with my 9.10 installs)

Anyhow, I will likely have unequivocal findings soon, but I hurry to post what I have thus far -- my corrections -- lest anyone out there make the wrong inference and act thereupon.

---

### Post by buntuyu on 2009-11-19
I have new findings/observations, but they are still non-conclusive; there is inexplicable behavior.

I reinstalled 9.10 Final and could not get into grub, with "F1" or anything else.

At one point with the beta, removing the battery and disconnecting power seemed to lead to the ability to get into the BIOS, but there could have been another reason.

I tried to install Fedora 12 on the same exact hardware and got failing results:  The installation DVD works all the way through if I install in text mode and with acpi disabled. ("linux text" and "acpi=off" for kernel options)


When Fedora 12 finishes installing, the first boot from hard drive failed, with an ever-blinking cursor. I ran the Fedora rescue and added "acpi=off 3" to grub.  Afterwards, the difference between Fedora and Ubuntu was that with Fedora the blinking-cursor state was not a freeze; one could power down with just a quick pressing of the power button.  With Ubuntu the blinking cursor indicates a hard freeze, requiring a long pressing of the power button.

Does anyone recognize these symptoms as indicative of some particular cause?

Any help greatly appreciated.  I have checked the BIOS availability for this, and, unfortunately, the last BIOS update was released in 2005, and this unit already has it (A05)

---

### Post by klemes on 2009-11-19
Don't know maybe look at the possibility of it being a hardware error.
Maybe it's the memory or a failing hard drive.
Have you considered this?

---

### Post by buntuyu on 2009-11-24
Just installed Ubuntu 9.04 on the M1400 (with "acpi=off").

Installation embedded the "acpi=off" into grub permanently, so it rebooted OK, from disk.  No power management, of course: shutdown command leads to "system halted", requiring one to press the power button physically to complete the shutdown (to power off)

will post any other further significant findings, if any occur.

The $1500 question right now, of course, is: will the system get hosed once I run system upgrade (and it upgrades itself to 9.10)?

thanks again for all your help.

---

