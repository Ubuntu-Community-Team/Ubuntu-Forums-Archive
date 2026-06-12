---
title: "Trying to access windows files by linux (one detail missing help plz)"
date: 2006-04-02
forum: General Help
---

### Post by raul_ on 2006-04-02
Hi.
I'm trying to access my windows files via linux. I almost got it. So what i did was mount my windows drive on a folder /mnt/win . If i access it from root i can open the files (read only). But i want to access them by gnome =( it says permission denied. I tried to change permissions (ug+x) but it doesn't change..a little help please.

---

### Post by NeghVar on 2006-04-02
assuming yr mount point/folder is in the media folder, type this into a terminal:

cd /media
sudo chmod 777 win

That should work, although I offer no guarantees or waranty.

---

### Post by raul_ on 2006-04-02
Thanks for the reply. Actually it's on the root folder =s i'll try to explain better:

i typed 

mount -t ntfs /dev/<mywindowsdrive> /mnt/win

on the terminal (as a root)

this allows me to access my windows files via linux. The problems is, i can't access them from the graphic environment, whick means that i can't use those files, let's say, to enque songs on xmms, to share my pictures, etc, because i don't have the necessary permissions.

I haven't tried your solution yet, does this change anything?

Thanks again ;)

---

### Post by fivedai on 2006-04-02
can  u try to add something into /et/fstab
/dev/hda*   /media/win    usr,utf8,umask=0   0 0    
the line above mybe wrong (i forget it)



or 

mount -t ntfs   -o usr,utf8  /dev/<mywindowsdrive> /mnt/win

---

### Post by aysiu on 2006-04-02
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

P.S. You can't *chmod* Windows partitions.

---

### Post by funkenstein on 2006-04-02
1. this guide hasn't failed me yet, provided you get the right disk in the /dev/hd[...] but you're unlikely to break anything by getting it wrong, provided you BAKUP your fstab!!!!!!!! (!!!!, for good measure :P):
[http://wiki.ubuntu.com/MountingWindowsPartitions](http://wiki.ubuntu.com/MountingWindowsPartitions)

2. is your windows drive formatted as NTFS or FAT? if NTFS, you can't write to it. If it's FAT 32/16 then you're ok.

Hope this helps.

---

### Post by raul_ on 2006-04-03
YESSSSSSS the post by aysiu worked :D:D  thanks to every1 else (i haven't tried those because the reply aysiu posted worked perfectly)  Good way to access your windows files =) u can't write to windows though...

---

