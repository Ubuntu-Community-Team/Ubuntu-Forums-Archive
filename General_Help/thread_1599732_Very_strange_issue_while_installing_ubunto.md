---
title: "Very strange issue while installing ubunto"
date: 2010-10-18
forum: General Help
---

### Post by bishoy02010 on 2010-10-18
[LEFT][SIZE=4]i have about 170 Gigabyte free at the last of my hard

i have windows 7 and suse linux installed on the machine

when i try to install ubunto

i start to create the partitions manually because i want to add it as a third operating system on my pc

anyway i create the 4 partitions /boot - / - /var - /home

automatically it choose to install the boot on sda  not sda 9 as the /boot was sda9

i click install 

it gives me this message " The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment. "

i burn another cd

and do the same ... the same problem

i try to create the partitions at the end of the hard disk not the beggining although im sure that there is no error in the hardware but the same message

lastly i change the boot to be created in sda 9

the same problem

when i do everything

i download Linux mint another operating system

and do the same points

the same error message appeared

by the way the boot is being damaged after restarting and i have to fix it from suse linux cd

do any one have a solution for this strange problem ?!!!

---

### Post by P4man on 2010-10-18
Can you please use a normal font size? If anyone has trouble reading default font, it will be for every post and he or she will increase font size for all posts.

Anyway, first Id make sure the harddisk is okay. From the live session go to system > administration>disk utility. Check the smart status of the drive.

If the drive is healthy, it could be cd (drive) issue. When you boot from the cd, right after the bios, hold down a key to bring up a menu. One of the options there is to check the cd for defects. Run that.

OH, and remove that email address, unless you want spambots to harvest it and bombard you with spam.

---

### Post by bishoy02010 on 2010-10-18
thanks a lot

and i will check them and tell you the results

---

