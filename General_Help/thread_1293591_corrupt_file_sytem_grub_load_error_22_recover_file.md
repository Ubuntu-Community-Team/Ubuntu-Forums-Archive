---
title: "corrupt file sytem grub load error 22 recover files"
date: 2009-10-17
forum: General Help
---

### Post by dayzmelttogether on 2009-10-17
Hi i am rather new to ubuntu, using it a couple months, i went and did something stupid,
i had ubuntu 8.10 as my only and main OS, i had all my files and such on that 1 partition, i put in my ubuntu .04 live cd and wanted to upgrade i realize u do that from the package manager i just wanted to see if i could well i wasnt payin attention and i told it to format, well as soon as the format menu appeared i powered down in hopes to save my files this is what i do know after some research.

regular boot gives me load error 22

gparted partition editor now sees the 107GB partition as unknown.

fdisk -l lists the parttion as a linux file system

super grub wont boot error 17

i can format the drive but i want to save my information, is there a way to restore the disk label and grub menu and hopefully save my previous installation of ubuntu?

all i have is my lap and a usb thumbdrive. 

thank you for your time.

---

### Post by mikewhatever on 2009-10-17
I doubt the partition label and boot menu has anything to do with the issue. You could try accessing the partition from the live cd, but if that doesn't work, you'll probably need to use photorec to recover the files.

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by dayzmelttogether on 2009-10-17
thank you ill give it a try and let the forum know how it goes...::prays::

---

### Post by dayzmelttogether on 2009-10-17
looks as though it would work everything looks like itll run smoothely,  however im in need of an external drive 80gb large , it is a shot in the dark but is their anothe way using the equiptment i have.

---

### Post by mikewhatever on 2009-10-17
Well, what tools do you have? Perhaps, if the partition hasn't been formatted, you could try partition table recovery.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)

---

### Post by dayzmelttogether on 2009-10-17
i have a toshiba sattelite laptop with a 100gb harddrive and a 2 gb thumbdrive ubuntu 9.04 live cd wich i am using now) and newly installed testdisk with photorec....if theres a way to restore the partiontable without formatting id deff wanna try that

---

### Post by dayzmelttogether on 2009-10-17
praise jesus, testdisk was able to restore the table thank you so much man and for all ur help. im not worried anymore i can see my files now XD now im sure i could find a tutorial but while this thread is here i might as well get it done right. how can i take my now mountable 100gb hd with damaged ubuntu installation and not rub boot loader and repair it?

---

### Post by mikewhatever on 2009-10-17
If the partition table is fixed you might be able to boot Ubuntu. If not, do you still get error 22? Can you also post the content of Grub's menu from your Ubuntu partition, located in /boot/grub/menu.lst and the output of the following commands:

sudo fdisk -l

sudo blkid

---

