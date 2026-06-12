---
title: "GRUB Error 13: Invalid or Unsupported Executable Format"
date: 2009-08-15
forum: General Help
---

### Post by example6 on 2009-08-15
I've set up a dual boot of Ubuntu 9.04 on my first hard drive and Windows Vista on the second one.

GRUB is installed on the first and the Vista bootloader on the second.

heres the output of 'cat /boot/grub/menu.lst':

```
default 0
timeout 30
title Ubuntu Linux
root (hd0,0)
kernel /vmlinuz root=/dev/sda1 ro

title Windows Vista Ultimate
rootnoverify (hd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader +1
```When I change Vista's root location to (hd1,0), Ubuntu won't boot.

I'm not sure what I'm doing wrong, if anybody's had the same problem or knows a solution please reply.

---

### Post by oldfred on 2009-08-16
Did you edit your menu.lst it is a lot different than any I have seen.

My ubuntu stanza based on my uuid and kernel verison:
title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
kernel        /vmlinuz-2.6.28-13-generic root=UUID=c00546bd-fa9c-4562-9785-5661da528114 ro quiet splash 
initrd        /initrd.img-2.6.28-13-generic
quiet

my windows entry for hd3 or sdd1:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows XP Professional
rootnoverify    (hd3,0)
savedefault
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1

grub error 13 info
[http://members.iinet.net.au/~herman546/p15.html#13]("http://members.iinet.net.au/%7Eherman546/p15.html#13")

---

### Post by darundal on 2009-08-28
I am also having the same issue, and the relevant bits of my menu.lst file are the same as what example6 posted, save for the fact that Vista has the word "loader" next to it.. That is straight from a fresh install of 9.04. If it helps at all I am using Vista Ultimate x64.

---

