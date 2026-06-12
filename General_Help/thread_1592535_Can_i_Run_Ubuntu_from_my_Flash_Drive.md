---
title: "Can i Run Ubuntu from my Flash Drive?"
date: 2010-10-10
forum: General Help
---

### Post by Japjeev on 2010-10-10
So i have a 16Gb Flash Drive and well i was wondering if i can make my ubuntu bootable from my flashdrive. SO if i go somewhere i have my Ubuntu with me with the programs installed in it. SO can i do this on my FlashDrive? if so how?

---

### Post by Japjeev on 2010-10-10
any help?

---

### Post by modafokaxx on 2010-10-10
Yes it is possible to install Ubuntu to a flashdisk.

You need to run the "Create startup disk" app located in the System menu.

Bear in mind though that the Ubuntu installed on the flashdisk will not be the same (nor in sync) with the one on your computer.
Think of it as another, separate computer, but one you can carry around in your pocket.


Also, please don't be so impatient, 20 minutes is not a very long time to wait for people to answer your questions... ;)

---

### Post by Japjeev on 2010-10-10
hehe lol sorry i am used to really active forums but right now i have windows xp i dont have Ubuntu install do u know a method for xp?

---

### Post by howefield on 2010-10-10
Have a look at unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oldfred on 2010-10-10
If you have 16GB you can do a full install, just like to another hard drive.

Shows Karmic but the same for any Ubuntu with slightly different screens now for Maverick.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

If you just want to boot multiple ISOs ( You can manually add this type of loopmount boot to a full install):
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 
Another - multibooting multiboot055.sh:
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

---

