---
title: "Windows inside of Ubuntu"
date: 2011-04-27
forum: General Help
---

### Post by grulex on 2011-04-27
i need a help about this one, i installed ubuntu inside of a windows ...and it wasnt hard .....

but now i have already installed ubuntu as a primary OS and no OS else, now i want to install windows beside it, and i dont know if i will have to format the whole hard disk, or it can be somehow separated a little of space from ubuntu just example 30GB's just to make a windows partition that i will use only with windows

btw i dont need to use them without restarting .....its ok i can restart PC to switch OS's .....so i dont need  a virtual box


any small tutorial ??? 
thanks in advance :D:D:D:D

---

### Post by AllGamer on 2011-04-27
Yes to all of the above.

but you have to decide which method you want to go for.

Obviously the easiest is to have Windows in a Virtual Box inside ubuntu (my preferred style)

But if you are into GAMES, then having windows as a real OS is easier.

You can have both Ubuntu + Windows in the same HDD, but then you'll need to repartition the HDD to give enough space for both

Windows itself is a big glutton it runs horribly with little space, if you are into games dedicate at least 300 GB just for windows

Also you'll need to be careful when installing windows, as it will definitely kill your grub2, which means you'll have to repair your ubuntu boot info; this is only applicable if you install both OSs into 1 HDD.

So, this means the best and easiest way to install windows + ubuntu on the same machine, is to have them each on its own hard drive, and at boot time you hit F8 or F10 or whatever is the key on your Motherboard is to choose which HDD to boot from.

and it and each other OSs will each be in its own dimension without messing around with each other data, partition & boot info.

that is the safest way.

on the Plus! side, if you do it this way, you can have VMware or other compatible Virtual boxes, to use the Windows HDD physically so, you will even be able to run the same Real windows inside ubuntu for non games stuff (but this will require some more knowledgeable VMware guru to set it up properly which is outside the scope of this topic)

---

### Post by AndyBoy_LV on 2011-04-27
You can resize your partitions without losing data by using one small utility called gParted. 

You can get a live CD from here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). Burn it, boot into it and it will be self-explanatory there. 

Good luck!

---

### Post by yetiman64 on 2011-04-27
> **AndyBoy_LV said:**
> You can resize your partitions without losing data by using one small utility called gParted.....

Gparted is good, but have a power outage while it is operating or make a mistake with it and you can say goodbye to a lot of your data. (Have had to reinstall OSes both Linux and Windows after mistakes were made myself, not to mention having to recover my data off backups).

OP, using gparted carries some risk and it always pays to back up your important data you can't afford to lose OFF the hard disk being re-partitioned as a precaution before using it. If nothing bad happens at least you have an up to date backup of your data :).

As you say in post 1 you only have Ubuntu on the drive, you most likely have an install disk for it so all should be OK. You will only really need to back up user generated data you don't want to lose (if a problem occurs) the OS can be easily re-installed in such circumstances.

---

### Post by aphatak on 2011-04-27
My suggestion would be to reduce the Linux partitions to a small size (I run Ubuntu desktop quite comfortably in a 16GB disk partition with room to spare), and make the Windows partition as large as possible.  The reason is simple - you can mount, read from and write to a Windows (NTFS) partition in Ubuntu, but you can't access an Ext4 drive from Windows.  This set up allows you to share data seamlessly between Ubuntu and Windows.

---

### Post by grulex on 2011-04-27
from all of this i have come to conclusion that easiest way is .......to format whole HDD put the windows first and then install ubuntu inside it ...as i did before

i dont have nothing that i must save on my HDD its just that i didnt want to delete ubuntu for nothing and then install it again and do the updating again and all the installations ...


but thanx anyway, i appreciate your answer, and the time u took to help me :):):):)

---

### Post by grulex on 2011-04-27
> **aphatak said:**
> My suggestion would be to reduce the Linux partitions to a small size (I run Ubuntu desktop quite comfortably in a 16GB disk partition with room to spare), and make the Windows partition as large as possible.  The reason is simple - you can mount, read from and write to a Windows (NTFS) partition in Ubuntu, but you can't access an Ext4 drive from Windows.  This set up allows you to share data seamlessly between Ubuntu and Windows.

can u like .....reduce linux partition while you'r using it? ....and leave some free space on HDD, or do u need to reinstall the OS ?

---

### Post by AllGamer on 2011-04-27
> **grulex said:**
> can u like .....reduce linux partition while you'r using it? ....and leave some free space on HDD, or do u need to reinstall the OS ?

not while it is running

that's why AndyBoy_LV suggested to use the Gparted live CD

you can do it when it is, not running.

but even if you did manage to shrink down Linux

when you install Windows, it will cause problem with the Grub2, then you'll need to rebuild your Grub2, to read both Windows and Linux partitions

that's why i suggested to have it on 2 separate HDD, it is a much cleaner setup and easy

---

### Post by shaft350x on 2011-04-27
If you are going to go the route of doing a fresh install I would suggest that you also make a separate partition for your /home directory.  Then if you want to do a fresh install of your Ubuntu OS you don't write over all your files.

(Not that you were actually asking for that suggestion, but if you are going to be tinkering with partitions this is useful)

As previous posters said, Live CD with gparted.

---

### Post by techunit on 2011-04-27
If you install Windows afterward your going to damage the mbr which will require you to reinstall grub. So if you aren't comfortable with the terminal at all you may want to do a clean format install windows first then install Ubuntu afterward.

If you really want to install Windows last you should look at this guide here
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by grulex on 2011-04-27
thank u all for your time and patience ...... i decided to install windows first and the ubuntu afterward .....

that seems like best solution ....

one more thing for the end... how do i move thread to "solved" ?

 or u do it if u can

---

### Post by AndyBoy_LV on 2011-04-27
You can press "Thread Tools" in the right upper corner of this topic and select "Mark this thread as solved"

---

