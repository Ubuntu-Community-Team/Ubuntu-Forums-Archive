---
title: "GRUB_DEFAULT, saved"
date: 2009-12-25
forum: General Help
---

### Post by Black_Moon on 2009-12-25
I have 2 OS on my notebook: WinXP & Kubuntu 9.10 (kernel Linux 2.6.31-16-generic)

Grub2 has new feature - ability to put value SAVED in GRUB_DEFAULT. (load last success OS).
I tryed so - but always had first menu point.

Here's my my grub menu-list:
> 
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Professional RU (on /dev/sda1)

And sda (320 Gb) has partitions:
> 
sda1 - ntfs (WinXP)
sda5 - ntfs
sda6 - ext4 (/)
sda7 - swap
sda8 - ext4 (/home) 
If previous OS was Linux - saved menu works, if WinXP - doesn't work - shows first line of menu-list.:(
How I can save WinXP as saved grub menu?
Thanks.

---

### Post by mikewhatever on 2009-12-25
Somewhat obvious, but did you run <sudo update-grub> after making the change?

---

### Post by Black_Moon on 2009-12-26
> **mikewhatever said:**
> Somewhat obvious, but did you run <sudo update-grub> after making the change?

Yes.

May be it hapens due partitions?

---

### Post by john newbuntu on 2009-12-26
Set it as follows (lowercase) in /etc/default/grub and run sudo update grub.
GRUB_DEFAULT=saved

---

### Post by Black_Moon on 2009-12-27
[B][john newbuntu]("http://ubuntuforums.org/member.php?u=956991")

[/B]Thanks a lot, lowcase works!! ++

> GRUB_DEFAULT=saved

---

### Post by j_keiter on 2013-03-08
First 'sudo update grub' did not work for me.  I had to 'sudo update-grub'.  Second 'GRUB_DEFAULT=saved' did not work.  Still booted to Ubuntu instead of Linux Mint after rebooting while using Linux Mint.  Last operating system used did not get saved and reloaded as supposed to.  Jason Keiter

---

### Post by wildmanne39 on 2013-03-08
Old thread closed! Please start a new thread you can link to this one if you need too.
Thanks

---

