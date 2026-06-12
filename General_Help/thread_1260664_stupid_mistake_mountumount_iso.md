---
title: "stupid mistake mount/umount iso"
date: 2009-09-07
forum: General Help
---

### Post by Unlearned on 2009-09-07
i was trying to get my system to mount an iso and accidentally mounted it just under /mnt now i want to know how to remove those files

and how to get the iso mount so my game sees it.

---

### Post by CatKiller on 2009-09-08
sudo umount /mnt

---

### Post by Unlearned on 2009-09-08
that unmounted it but the files are still there

---

### Post by ryotakatsuki on 2009-09-08
Uhm... which files are you referring to? If the iso was umounted correctly, there shouldn't be any left file in /mnt unless you had some there before first mounting it.

---

### Post by Unlearned on 2009-09-09
the files from the iso are still there i thought they would go when it unmounted but they did not and they are read only haha no deleting.

will have to go in and change the permissions i guess so i can get rid of them

---

### Post by ryotakatsuki on 2009-09-09
If the iso was unmounted the files shouldn't be there. Could you execute:

df -h 

And post the output here?

Cheers.

---

### Post by Unlearned on 2009-09-09
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             166G  128G   30G  82% /
varrun                1.8G  132K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   76K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   40M  1.7G   3% /lib/modules/2.6.24-24-generic/volatile
/dev/sda1             3.0G  647M  2.4G  22% /media/sda1
/dev/sda2             121G  117G  3.8G  97% /media/sda2
/dev/sda1             3.0G  647M  2.4G  22% /media/sda5

---

### Post by Unlearned on 2009-09-09
ok i ran that command and the files were still there even after restart....

now a few days later they are gone....computers strange and wonderful

thank you for your help

---

### Post by Unlearned on 2009-09-09
ok now that that is working i got the files to mount and unmount when i want. 

i put the new mount point under cdrom and it shows up as a disk on computer, but diablo 2 does not see it as a disk yet

i used:
 sudo mount -o loop Expansion.iso /media/cdrom/Expansion

is there a step i missed to get it to act as a disk for the game?

---

### Post by hawthornso23 on 2009-09-09
The Diablo II Lord of Destruction Expansion disk is a securom protected disk. The orginal disk included non-standard data. An ISO made from this disk includes this non-standard data and you need special tools to mount it. You cannot just mount it the way you mounted the other Diablo II ISO files with mount -t iso9660 -o loop. AFAIK there is no tool within linux that will mount ISOs made from securom protected disks as securom protected stuff is not common in the linux world. In the windows world things like daemon tools lite exist which will mount this kind of ISO.

Having said that there is a way. But you need a network with a windows machine on it - even a 2 machine network with a laptop would do. Install daemon tools lite on the windows machine and mount the ISO there. Share the virtual drive across the windows network. Install samba on the linux machine. You'll be able to see the shared virtual drive on the network and open it and read the files. And you can even mount it and tell wine it is a cdrom and install software from it. I've done it and it works, but it isn't easy. 

I can't quite recall the details now. There is a thread on these forums that tells how to do it. It is fun to do and quite amazing that it works. Have fun.

> **Unlearned said:**
> ok now that that is working i got the files to mount and unmount when i want. 

i put the new mount point under cdrom and it shows up as a disk on computer, but diablo 2 does not see it as a disk yet

i used:
 sudo mount -o loop Expansion.iso /media/cdrom/Expansion

is there a step i missed to get it to act as a disk for the game?

---

### Post by Unlearned on 2009-09-09
ok thank you

i guess it is easier just to use my actual disk.

---

### Post by hawthornso23 on 2009-09-09
> **Unlearned said:**
> ok thank you

i guess it is easier just to use my actual disk.

Indeed.

---

