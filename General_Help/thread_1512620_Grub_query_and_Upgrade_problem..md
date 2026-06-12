---
title: "Grub query and Upgrade problem."
date: 2010-06-18
forum: General Help
---

### Post by tattushenoi on 2010-06-18
I am relatively new to Linux. Only a few weeks old. I had Karmic Koala installed on my system along with windows xp. I have 3 partitions. 15Gb for Linux. 18 for XP and one 43 Gb for data. 

I upgraded to Lucid Lynx recently. I have 2 queries.

1) In Karmic Koala I had set passwords to open my partitions. But after I upgraded to Lucid Lynx, the partitions are opening without asking for a password. But if I try to install a program it asks for authentication. Only while opening a partition it is not asking anything.

I want Ubuntu to ask for a password everytime I open a partition. What should I do?

2) After the upgrade I chose to keep the 'present version of grub' when asked for choice[maintainers version etc etc]. But now I get to see the option for Karmic Koala login as well in grub. But if I try to select that it says there is no such thing installed and rightly so. I want that extra option removed as Karmic Koala is no longer there. 

Please provide suggestions.

---

### Post by tattushenoi on 2010-06-18
To add about the Grub problem, I got this when I ran sudo update-grub.


tattushenoi@TATTUS:~$ sudo su
[sudo] password for tattushenoi: 
root@TATTUS:/home/tattushenoi# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda2
done
root@TATTUS:/home/tattushenoi# 

[IMG]file:///home/tattushenoi/Desktop/Screenshot.jpeg[/IMG][IMG]file:///home/tattushenoi/Desktop/Screenshot.jpeg[/IMG]

---

