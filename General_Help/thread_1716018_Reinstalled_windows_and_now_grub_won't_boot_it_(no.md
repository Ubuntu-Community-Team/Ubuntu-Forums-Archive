---
title: "Reinstalled windows and now grub won't boot it (no such device)"
date: 2011-03-27
forum: General Help
---

### Post by Mi11z on 2011-03-27
Hello,

So here is the story after the dreaded Microsoft service pack update I found myself with a deactivated version of windows and after trying everything my only solution was to do a clean install of windows 7 service pack one, so I did this everything worked fine but then the windows bootloader tookover again, so I used this method to fix that:

> How to restore the Ubuntu grub bootloader (9.10 and
beyond)
First you need to find out what your drives are called. You can do this by going to a terminal and typing:
Code:
sudo fdisk -l
From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8242;&#8242;.
So, still in the terminal, type:
Code:
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
And then, to reinstall the grub:
Code:
sudo grub-install --root-directory=/media/sda5 /dev/sda
Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8242;&#8242; and &#8220;/dev/sda&#8221; with what you found in the
fdisk output.


Like I've used before the only problem now is after doing this and reinstalling grub, when I select Win7 in grub I get the no such device error, so I'm pissed because now I can't boot windows when I was just getting back to normal, the good news is I can still boot ubuntu with nothing but a minor graphics error on the way in but that doesn't effect anything anyway.

so please help me cause I really need to get back to my windows partition!

also, nothing on the Win7 partition has been touched/deleted because I can access it from here in ubuntu right now and everything is still there, the bootloader just needs pointing at the partition again I think.

OK guys so PLEASE HELP ME ASAP!

:(

---

### Post by oldfred on 2011-03-27
Did you do this, it may be still looking for the old version.

sudo update-grub

If that does not work post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by billbear on 2011-03-27
sudo update-grub

---

### Post by Mi11z on 2011-03-28
Thanks guys just tried the first solution you guys gave, get back to you after a reboot. :)

***********************************************EDITED*********************************************************

Yep that first solution from both you guys worked, so panic over and I'll make a note of that so I remember next time, cause I quite often forget to "sudo update" things like burg not just grub, so thanks again guys later. :) :D

---

### Post by dragonfly41 on 2011-03-28
I'm using Ubuntu 10.10 in demo mode (sessions lost each time)

Can someone explain when I run above command why I get this

```

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

```

I'm in dual boot mode but not a full installation of Ubuntu .. I stay in Demo Mode.

and here are the partitions ..

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          25      200781   de  Dell Utility
/dev/sda2              26        1331    10485760    7  HPFS/NTFS
/dev/sda3   *        1331       30075   230888444    7  HPFS/NTFS
/dev/sda4           30075       30402     2621440    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
ubuntu@ubuntu:~$ 


```

---

### Post by oldfred on 2011-03-28
You cannot run sudo update-grub from liveCD. That is run from your install as it writes a new grub menu file grub.cfg. Of course it cannot write a new file to the CD. If you want to run it on your install you have to chroot into your install.

---

