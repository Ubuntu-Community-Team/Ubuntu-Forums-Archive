---
title: "Help duel booting Ubuntu and Gentoo!"
date: 2010-02-17
forum: General Help
---

### Post by wqawasmi on 2010-02-17
Alright I just spent 8 Hours getting my Gentoo system up and running. I decided to skip the GRUB Installation part, because I thought GRUB2 that came with my Ubuntu 9.10 would just detect it and allow me to boot up. 
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Windows 7 (loader) on /dev/sda1
Found Gentoo Base System release 1.12.13 on /dev/sda5
done

```
I ran update-grub, it detected Gentoo, I rebooted but the option was not there.

I tried to add an entry manually in /etc/grub.d/40_custom, at first it showed up in GRUB2, but did not boot up. It gave me the "FILE DOES NOT EXIST" error. 
```
 #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Gentoo" >&2
cat << EOF
menuentry "Gentoo 2.6.31-gentoo-r6" { 
set root=(hd0,5) 
linux /boot/kernel-2.6.31-gentoo-r6 root=/dev/sda5
} 
EOF

```
I tried again and again, until at one point, GRUB2 just gave me the finger and stopped showing the Gentoo entry when I boot up. 


My Gentoo Partitioning Scheme: 

Boot=/dev/sda7
Swap=/dev/sda6
Rest Of System=/dev/sda5

Tips, Help? I spent a long long time getting Gentoo working, would be a shame to have all of that gone to waste. 
If you can go easy on me with the GRUB Terminology, I have never been fond of it. 

Thank You,

-Will Qawasmi

---

### Post by ajgreeny on 2010-02-17
Try changing the entry in 40_custom that is shown as (hd0,5) to (hd0,7), as follows
 > #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Gentoo" >&2
cat << EOF
menuentry "Gentoo 2.6.31-gentoo-r6" { 
set root=(hd0,7) 
linux /boot/kernel-2.6.31-gentoo-r6 root=/dev/sda5
} 
EOFAt the moment (hd0,5) is pointing to rest-of-system as you called it, grub2, confusingly naming disks from 0, but partitions from 1, so wherever you got the gentoo partitioning scheme from, and I assume it was fdisk, you are not pointing grub at the boot partition, which in grub2 terms would be as above, (hd0,7)

I hope that makes some sense to you, but even if it does not work you have lost nothing, as you can't boot to gentoo at the moment anyway, and hopefully you will have learned a little more about grub2.  I am surprised, however, that update-grub in ubuntu did not get gentoo to be added successfully.

---

