---
title: "partition problem"
date: 2009-09-17
forum: General Help
---

### Post by yulai84 on 2009-09-17
Hello,  i have a problem with the ubunto installation, its a XP-Ubuntu partition, it seems it was made on a very small partition or something similar because when i try to install updates or any other program it tells me there is not enough memory, the free space is just around 50 mb while the XP OS reports 139 GB, the hard drive is around 150 GB, i cant reinstall the ubuntu,the boot run from windows doesnt work anymore y sends me straight to the ubuntu OS and im not sure how to use the Gparted to redistribute de partition, the only option it shows for the NTFS, which is the big partition now, is to format. Ireally dont know what to do and dont want damage the hard drive severly, if anyone could help it would be much appreciated.

thanks

---

### Post by wilee-nilee on 2009-09-17
So it sounds like from your description that you had XP and you dual booted with Ubuntu, if this is the case grub should be your booting controller. If you run sudo update-grub in the terminal it should load the XP. But your partition sounds to small for the Ubuntu to be workable. If all of this is correct you can reinstall Ubuntu after reformatting the partitions in other words shrink the windows partition leave the rest blank for the install of Ubuntu. The key thing here is that after you shrink XP and before you install Ubuntu start XP and defrag it, close put your Ubuntu CD in and when you get to the partition size choice, choose side by side and move the bar at the bottom to the size it is set at with the partitioning so that the XP is basically left alone. Grub will then be your boot-loader. 

I realize you said that a reinstall is not a option, but the description doesn't make sense to me, in that if you installed Ubuntu last the problems your having with XP not showing is with the Linux Grub and the sudo update-grub command should work if everything is in order. I suspect that the only 50 mb space left is the culprit in this, but that is a uneducated guess. Hopefully others will comment and you can get this worked out.

Also Gparted will tell you exactly how big the hard drive is and you can see the amount each partition is full, Gparted wont do anything until you tell it to so be careful and post whats going on.

---

### Post by P4man on 2009-09-17
If I understand it right, you did a WUBI install, and your ubuntu (virtual)  partition is too small and full.  When you do a wubi install, you dont actually change partitions, you make a virtual partition inside your windows host, which is just a big file to windows, and which ubuntu will mount as if it was a partition.

I dont know how to resize that, certainly not with gparted as it isnt a partition,  but after some googling, it looks hard. Your best bet seems to be to move your ubuntu to a real partition:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by yulai84 on 2009-09-17
Thank you Wilee for such a fast reply, i realize i was not very specific, not used to the language, all this is new to me until today. In fact i did the dual boot and used the option help with boot in which the ubunto disk installs a program to initiate the boot, not manually nor inmediately, then at the installation part where the partition bar choice appears i was very uncatious and went ahead without realizing what was it about, so the result was hd has the smallest partition possible to let ubunto run, i want to change that so went to XP did defragmentation and back to ubunto downloaded and installed gparted. Gparted shows 3 partitions FAT32 with 4.88 GB, then ntfs (the one with XP i suppose) with 141.6 and then extended with 2.5 GB, this one divided in ext3 and linux-swap, so my inttnrion was to redimension the ntfs partition but the only option i have is to format, sounds pretty drastic to me, the extended cant be modified and the fat 32 accepts every modification, redimension, delete, copy, format, etc. How can i make larger the ubunto partition at this piont, since it has only around 50 MB free space and is useless that way?

---

### Post by wilee-nilee on 2009-09-17
> **yulai84 said:**
> Thank you Wilee for such a fast reply, i realize i was not very specific, not used to the language, all this is new to me until today. In fact i did the dual boot and used the option help with boot in which the ubunto disk installs a program to initiate the boot, not manually nor inmediately, then at the installation part where the partition bar choice appears i was very uncatious and went ahead without realizing what was it about, so the result was hd has the smallest partition possible to let ubunto run, i want to change that so went to XP did defragmentation and back to ubunto downloaded and installed gparted. Gparted shows 3 partitions FAT32 with 4.88 GB, then ntfs (the one with XP i suppose) with 141.6 and then extended with 2.5 GB, this one divided in ext3 and linux-swap, so my inttnrion was to redimension the ntfs partition but the only option i have is to format, sounds pretty drastic to me, the extended cant be modified and the fat 32 accepts every modification, redimension, delete, copy, format, etc. How can i make larger the ubunto partition at this piont, since it has only around 50 MB free space and is useless that way?

So as the other post suggests which I wondered about myself you have not done a Wubi install. Gparted only works on unmounted partitions so you can use your live CD or a Gparted download ISO and burn a disc. I am not sure what all the partitions are but you can down load  supergrub  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

which will actually allow you to open the smaller fat32 to see what it is and the others. I suspect the Fat 32 is a separate partition for whatever. If you go to the home portion of your Ubuntu install do the other Volumes (name for partitions in Linux) show up if so you can double click and look in there and see what they are. Can you post a screen shot of the Gparted gui.

Edit: So as I thought a little more I wonder if the Fat32 is the recovery partition for XP, I have not bought a new computer ever so I am not familiar with how factory window installs go, but since they don't provide discs now they use a partition with the information. So if this is the case personally I would leave it there, then delete the Ubuntu part with the Gparted disc or Gparted in a Ubuntu live CD, then shrink XP to where you want, boot into XP defrag again after resizing then install Ubuntu with the live disc. I think you understand the side by side partition option and the slider to set the partitions where you want them. The last thing I would say to is that if there is anything on any of the operating systems you can't afford to lose then save them off the computer. I have never lost anything doing these sort of activities but others have.

---

### Post by yulai84 on 2009-09-17
sure im figuring out how to take a screenshot an post it

---

### Post by yulai84 on 2009-09-17
Couldnt post the screenshot, gave up on that already, im going to try that last suggestion you wrote, will delete the ubuntu part and try reinstalling,

Thank you so very much for your time and help, will post my results for sure

---

### Post by wilee-nilee on 2009-09-17
> **yulai84 said:**
> Couldnt post the screenshot, gave up on that already, im going to try that last suggestion you wrote, will delete the ubuntu part and try reinstalling,

Thank you so very much for your time and help, will post my results for sure

Good Luck, I don't know the percentage of people who go straight for a dual boot when Wubi is an option, although the Ubuntu program is faster, safer, and able to access the XP partition when it is in its' own partition. The cool thing about this access is that if you have something that wont delete in XP generally accessing it through a Linux setup will allow you to delete to your hearts content.

---

