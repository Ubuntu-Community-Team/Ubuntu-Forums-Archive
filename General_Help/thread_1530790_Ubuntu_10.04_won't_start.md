---
title: "Ubuntu 10.04 won't start"
date: 2010-07-14
forum: General Help
---

### Post by skarme on 2010-07-14
I have a 149.05 GB hard disk, with 5 partitions. Windows XP installed in C: [48.83 GB], D, E and two partitions for Ubuntu 10.04 (20.20 GB, 942 MB swap space).
I was working on Ubuntu when because of a power failure, the PC shut abruptly.
After restoration of the power supply, I started the PC and I wasn't able to boot into Ubuntu.
This is what my GRUB menu looks like:
```

GNU GRUB version 1.98 - 1ubuntu5
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
Microsoft Windows XP Professional (on /dev/sda1)

```
I can boot into Windows XP with no issues, not the same with Ubuntu. When I enter the first option of the GRUB, this is what I get:
```

Mount: Mounting /dev/disk/by-uuid/0cc7fb0d-761d-4039-a89a-7c7836688ba3 on /root
failed: Invalid argument.
Mount: Mounting /dev on /root/dev failed: No such file or directory
Mount: Mounting /sys on /root/sys failed: No such file or directory
Mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Tr passing init=bootary
BusyBox v1.13.3 (Ubuntu 1:1.13.3 - 1ubuntu11) built-in
shell9ash)
Enter 'help' for a list of built in commands.
(initramfs)

```
I have been working on Ubuntu for more than a year and I want it back. However I don't want to mess around with the Windows or other partitions for that matter. Can anyone help me with this please. I would be highly grateful if the solution is explained to me in a lucid way, never dealt with such issues before. Thanks in advance.

---

### Post by lordskid on 2010-07-14
next time you boot, highlight your ubuntu entry

```
Ubuntu, with Linux 2.6.32-21-generic
```
then press 'e'

then kindly post the output here. I'm fascinated why your system is mounting dev,proc... and etc to /root when it should mount to /

---

### Post by skarme on 2010-07-14
> **lordskid said:**
> next time you boot, highlight your ubuntu entry
 
```
Ubuntu, with Linux 2.6.32-21-generic
```
then press 'e'
 
then kindly post the output here. I'm fascinated why your system is mounting dev,proc... and etc to /root when it should mount to /
Here is the output:
```

recordfail
insmod ext2
set root='(hd0,7)'
search --no-floppy--fs-uuid     --set 0cc7fb0d-761d-4039-a89a-7c7836688\
ba3
linux /boot/vmlinuz-2.6.32-21-generic root=UUID = 0cc7fb0d-761d-4039 -a\89a-7c7836688 ba3 ro        quiet splash
initrd /boot/ initrd.img - 2.6.32-21-generic.

```

---

### Post by m4tic on 2010-07-14
Try this
[http://ubuntuforums.org/showthread.php?p=9059244#post9059244](http://ubuntuforums.org/showthread.php?p=9059244#post9059244)

---

### Post by lordskid on 2010-07-19
```

recordfail
insmod ext2
set root='(hd0,7)'
search --no-floppy--fs-uuid     --set 0cc7fb0d-761d-4039-a89a-7c7836688\
ba3
linux /boot/vmlinuz-2.6.32-21-generic root=UUID = 0cc7fb0d-761d-4039 -a\89a-7c7836688 ba3 ro        quiet splash
initrd /boot/ initrd.img - 2.6.32-21-generic.

```

have you solved this problem?

try changing above to 
```

recordfail
insmod ext2
set root='(hd0,7)'
linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7 ro quiet splash
initrd /boot/initrd.img - 2.6.32-21-generic.

```
kindly see what key combination to use to boot i think its ctrl-b

---

### Post by skarme on 2010-07-19
Well I solved the issue, reinstalled GRUB. Thanks for the suggestion anyway [lordskid]("http://ubuntuforums.org/member.php?u=665678").

---

