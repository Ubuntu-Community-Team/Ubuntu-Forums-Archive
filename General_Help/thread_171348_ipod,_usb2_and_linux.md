---
title: "ipod, usb2 and linux"
date: 2006-05-06
forum: General Help
---

### Post by linuxted on 2006-05-06
I'm desperate.  My ipod no longer is visible (in fact it causes the system to have to reset before a reboot is possible) when I connect to usb2.0 on my ubuntu linux machine.  

I can see the device if I do a sudo rmmod ehci_hcd

However, I am no longer able to add songs to the ipod, even after restoring the software on a windows machine.  ANY help is appreciated!  I've tried the following procedure, but it did not work:  

0) restore ipod in windows
0b) write some songs to the ipod in windows (may not be needed)
1) reboot linux machine
2) sudo rmmod ehci_hcd
3) plug in ipod
3b) Then clean up the directories:
   dosfsck -a /dev/sda2   (might be sdb2, check with fdisk -l or dmesg)
4) Start gtkpod and read from the ipod
5) Write some tunes
you *might* have to run the following
cd /media/ipod/iPod_Control/Music
Create these directories (can be as root or tburmas, it doesn't matter)
mkdir F01  - F19
6) exit gtkpod
7) unplug the ipod, reboot and then see if it will connect without
doing the USB1.0 trick.  If it does, great.  If not, you're in for
some sloooooooooow transfers
8) You will have to ALWAYS use rmmod ehci_hcd BEFORE plugging in the
ipod and AFTER reboot if the USB2.0 method won't work.

Thanks,
linuxted:-x

---

### Post by linuxted on 2006-05-18
[QUOTE=linuxted]I'm desperate.  My ipod no longer is visible (in fact it causes the system to have to reset before a reboot is possible) when I connect to usb2.0 on my ubuntu linux machine.  

I can see the device if I do a sudo rmmod ehci_hcd

However, I am no longer able to add songs to the ipod, even after restoring the software on a windows machine.  ANY help is appreciated!  I've tried the following procedure, but it did not work:  

0) restore ipod in windows
0b) write some songs to the ipod in windows (may not be needed)
1) reboot linux machine
2) sudo rmmod ehci_hcd
3) plug in ipod
3b) Then clean up the directories:
   dosfsck -a /dev/sda2   (might be sdb2, check with fdisk -l or dmesg)
4) Start gtkpod and read from the ipod
5) Write some tunes
you *might* have to run the following
cd /media/ipod/iPod_Control/Music
Create these directories (can be as root or tburmas, it doesn't matter)
mkdir F01  - F19
6) exit gtkpod
7) unplug the ipod, reboot and then see if it will connect without
doing the USB1.0 trick.  If it does, great.  If not, you're in for
some sloooooooooow transfers
8) You will have to ALWAYS use rmmod ehci_hcd BEFORE plugging in the
ipod and AFTER reboot if the USB2.0 method won't work.

Thanks,
linuxted:-x[/QUOTE]

anyone?

---

### Post by halfvolle melk on 2006-05-18
No clue, I don't have an iPod, but more users seem to have issues with gtkpod and use Banshee. Maybe that works for you.

---

