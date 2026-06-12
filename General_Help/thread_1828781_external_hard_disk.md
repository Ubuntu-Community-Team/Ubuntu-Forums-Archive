---
title: "external hard disk"
date: 2011-08-19
forum: General Help
---

### Post by rahulbest on 2011-08-19
i have 320 GB external USB hard disk...i want to install ubuntu on it and it should get booted if i connect to pc that i want...how to do that?

---

### Post by Duncan Williams on 2011-08-19
As far as I know. If you install ubuntu to your external drive it should be bootable from grub.
Someone should correct me if I have missed something or am incorrect.

---

### Post by Basher101 on 2011-08-19
now do you want the whole drive for linux? or do you want a partition where it is on so you can store data on the rest of it? ofcourse you can boot ubuntu like this - you must only be ***_VERY_*** careful where you install the bootloader to during the installation proccess. When you have installed it on your external hdd it will show up GRUB2 and you would boot automatically into ubuntu if you dont select something (you have 10 seconds during bootup to choose). Otherwise this is a very good way to keep your windows on your internal hdd untouched from partitioning. Just be careful that you select _/dev/sd***b***_ for the partitioning and the bootloader

*edit* - if you boot from a Live usb stick instead of a CD your external HDD can also show up as /dev/sd***_c_***. just keep looking at the total capacity (it will show you the 320gb total). if you read through everything carefully you should not mess up

---

### Post by rahulbest on 2011-08-19
thnks for help....
can u give me step by step method or some link

---

### Post by oldfred on 2011-08-20
If you install a different version the screens may be slightly different but the process is the same.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

You want to use manual install as that is the only way you get the extra combo box that lets you choose to install grub2's boot loader to the external drive.

---

