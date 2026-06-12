---
title: "Need Help with ubuntu re-installing/partition resizing (URGENT)"
date: 2010-05-28
forum: General Help
---

### Post by Benjamin B on 2010-05-28
Hi!

I started with Ubuntu 9.10 one week ago and had some problems with the desktop display, so I decided to swich to Lucid Linx, and then figure out the problem... bad decision... The update failed and since then I was no longer able to execute the updater. So I decided to re install 9.10 from the live CD I first used... bad decision again... During the installation I realized that Ubuntu would not reinstall over the last one, but would create yet another partition, so I aborted (after the partition instance, which is probably what caused the major blow-up). Now I must tell you that, since the first installation, I chose a dual boot with Vista. NOW HERE IS MY PROBLEM: After I aborted the second installation I rebooted and now I just get an error message from GRUB that says "filesystem unknown" or something like that. So now I am working from the live CD, which is the only thing I can do in my computer... I either need to erase all the partitions and GRUB and leave Windows alone, which I DESPERATELY need for work, or somehow go back  to the dual-boot-working last version. I really want to start using Linux, but I have realized I need to take some classes before. PLEASE somebody help me get my working computer back!
This is my mail account: **************, if somebody is willing to contact me and chat, that would be great. If so, just leave a message in this threat and add me to you messenger/yahoomessenger/whatever contact list.

THANKS A LOT,
Benjamin.

---

### Post by dino99 on 2010-05-28
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

note: remove your mail if you dont want spam overflow

---

### Post by Benjamin B on 2010-05-28
Thank you dino99, but the instructions in the Parted Magic website are far too complicated. I hope there is a simpler way, I just want to be able to work again.

Benjamin.

---

### Post by lmarmisa on 2010-05-28
I recommend you to reinstall ubuntu selecting manually the partition for root (/).

Follow the standard steps until the Prepare disk space menu.

Pay attention here. You have to chose the option "Specify partitions manually (advanced)" in this menu and Forward.

Then try to select the first Linux partition of type EXT3 or EXT4, click on Change and select Use as:  Ext3, tick Format the partition and Mount point: /. Do not change the partition size. I attach an image of this critical step. Finally Ok.

You can see a second image attached after the previous step.

Continue with the installation until its completion.

I think that your problem is not difficult to solve.

Best regards,

Luis

---

### Post by Benjamin B on 2010-05-28
Thanks Luis,

I have done what you say, but I haven't installed it because, before I do it, I wanted to know how to get a dual boot in manual configuration.
Here I attach a picture of the final partitions (dev/sda1 is Vista).

Regards,
Benjamin.

---

### Post by oldfred on 2010-05-28
It should work just fine. Just be sure to install grub to sda only by clicking on advanced button.

Full example:
Dual Boot win/10.04
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Advanced button 
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)


Sometimes we recommend additional partitions for /home or shared data if you want some data to be easily accessible by both windows & Ubuntu but they are not required.

---

### Post by Benjamin B on 2010-05-29
With the help of lmarmisa I reinstalled Ubuntu 9.10, manually resizing the partitions. In the post of lmarmisa you can see the process more detailed.

Thanks for your help,
Benjamin.

---

