---
title: "Help with locked micro sdhc partition"
date: 2012-09-25
forum: General Help
---

### Post by gV57gt7K5f on 2012-09-25
So I was writing the raspberry pi image to my micro sd using the steps here: [http://elinux.org/RPi_Easy_SD_Card_Setup](http://elinux.org/RPi_Easy_SD_Card_Setup)
and the command: dd bs=1M if=~/2012-09-18-wheezy-raspbian.img of=/dev/mmcblk0

it seemed to work but i couldnt boot, so i tried to delete the partitions and try again. but everytime i delete them and refresh, they both are still there. i tried using gparted and fdisk
after a while i even resorted to using:
shred
dd if=/dev/zero of=/dev/mmcblk0
but still nothing

DBAN and windows cant do anything either

the adapter works fine on my other micro sd and: yes i did check to see if the switch was set to lock

Please help!

---

### Post by gV57gt7K5f on 2012-09-25
bump anybody?

---

### Post by gordintoronto on 2012-09-25
Did you try moving the switch to the other position? Can you write to the micro SD on other systems or devices?

In my experience, when you run sudo gparted, it has full command of any storage device.

---

### Post by Mark Phelps on 2012-09-26
What kind of device are you using to read the SD Card?

I've found that internal memory card readers are inherently unreliable in Linux.  I've tried several and, one day they work, the next day, they don't.

I've had to resort to an external, USB-connected, memory card reader -- and it works every time, with every memory card I have used.

---

### Post by gV57gt7K5f on 2012-09-26
yes i checked the switch.
The adapter works fine on my other micro sd card
and i tried on my friends computer too

so i know the card is the problem

---

