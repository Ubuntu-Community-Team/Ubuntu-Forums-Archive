---
title: "Dual boot / Gruber problem"
date: 2009-12-01
forum: General Help
---

### Post by Mikael Gustafsson on 2009-12-01
Hi!

I need some help with gruber in my ubuntu 9.04. 
I have had ubuntu installed on my computer for 8 month now with out any problem. But i bough a video editing program that did work with WINE so i hade to install windows XP on my second hard disk. Now is the problem like this: 
1) If i disconnect the sata cable that goes to my ubuntu disk windows start up and i can run it. 
2) If both sata cables are connected ubuntu start up. 
3) Windows is located on hdb1

I have edit my meny.lst in gruber dir with the following last in file:
########
title Windows XP
root  (hd1,0)
makeactive
chainloader +1 

#########

But when i select the Windows XP at start up it does not start, it only says "Starting Up..." and noting happens. 

Can anyone help me?

---

### Post by john newbuntu on 2009-12-01
To start with, just get into Ubuntu and run this from a terminal
sudo update-grub

---

### Post by oldfred on 2009-12-01
Grub legacy is not as good as grub2 at finding other systems.

I think all you need to do is add map commands, if the boot flag * is on the makeactive is not required. Rootnoverify is preferred for NTFS partitions.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
[COLOR=Red]rootnoverify[/COLOR]    (hd1,0)
savedefault
[COLOR=Red]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader    +1

---

### Post by Mikael Gustafsson on 2009-12-02
Thx for the help!

I got it to work yesterday with the map thing. :)

Many thanks
Mikael

---

