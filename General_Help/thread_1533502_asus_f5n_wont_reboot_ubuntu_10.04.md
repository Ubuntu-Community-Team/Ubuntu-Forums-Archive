---
title: "asus f5n wont reboot ubuntu 10.04"
date: 2010-07-18
forum: General Help
---

### Post by savarkar on 2010-07-18
Hi all, 

I have ubuntu 10.04 on my laptop ASUS F5N. There was a bug in the past versions of ubuntu - ubuntu freezed while it was rebooting and solution is  [here]("http://ubuntuforums.org/showthread.php?t=716371"). However in 10.04 problem still remains, but now there is Grub 2 and mentioned solution does not work. At least I dont know how to apply those instruction for Grub2. Does anybody know?

Thank you for answer.


Old instructions:
> 
First method
1. at grub boot menu press e
2. go to 2nd line (root=...) and and press "e"
3. at the end of the line add "all_generic_ide" and press "enter"
4. press "b" to boot

Second method
Note : You may add the above command "all_generic_ide" to /boot/grub/menu.lst on the end of line root=
open console and tape:
1.sudo gedit /boot/grub/menu.lst
2.go to the line:

kernel /boot/vmlinuz-2.6.xx-xx-generic root=UUID=xxxxxxx-xxxxx-xxxx-xxxx-xxxxxx ro quiet splash

and the end of line tape this:

all_generic_ide


---

### Post by fwoncn on 2011-01-03
bump.

this problem's been affecting me too, for a long time. Grub2 only has /boot/grub/grub.cfg and it's quite different from the former config file - menu.lst.

---

