---
title: "Access Windows files"
date: 2011-06-02
forum: General Help
---

### Post by CovaDax on 2011-06-02
First off, I'm new to linux lol. I just installed Ubuntu 11.04 (from 10.04) inside the same partition as windows, and I was wondering how I could view the Windows files. 

I was able to do this back in 10.04 so I figure it's just a setting I need to tweak or something. I hope, lol. Anywho, if anyone can help out it'd be appreciated.

---

### Post by wgarcia on 2011-06-02
You should be able to see the windows the partition in the File Browser (left panel, as "File System" or something). Clicking on it should mount it and you should be able to browse your files there.

---

### Post by theprofessor102 on 2011-06-02
> **CovaDax said:**
> First off, I'm new to linux lol. I just installed Ubuntu 11.04 (from 10.04) inside the same partition as windows, and I was wondering how I could view the Windows files. 

I was able to do this back in 10.04 so I figure it's just a setting I need to tweak or something. I hope, lol. Anywho, if anyone can help out it'd be appreciated.

in terminal type fdisk -l, get the proper device number of hd 


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001    7  HPFS/NTFS

then you can mount 

mount /dev/sde1 /mnt

cd /mnt
and its all there.

---

### Post by webofunni on 2011-06-02
Open your file manager and check the disk in the left panel. Click on it and nautilus will mount that automatically.

---

### Post by CovaDax on 2011-06-02
Ah, I downloaded File Manager and that did it, thanks a lot!

---

### Post by CovaDax on 2011-06-02
lol false alarm. It looked the same.

I don't see anything about a disk in the file manager. All I see are linux files, but when I check my partitions there's still only one.

---

### Post by Rubi1200 on 2011-06-02
You should be able to access the files like this:

Open the Home folder and on the left-side go to Computer > File System > Host

---

### Post by CovaDax on 2011-06-02
I can't seem to find that directory. There's nothing called File System

---

### Post by CovaDax on 2011-06-02
Ah, if I use File Manager I see it. And I found the files, thanks a lot :D

---

### Post by Rubi1200 on 2011-06-02
> **CovaDax said:**
> Ah, if I use File Manager I see it. And I found the files, thanks a lot :D

No problem, you're welcome :)

---

### Post by vhradice on 2011-06-03
The windows disks need to be mounted in order to look at/change (yes, you can change stuff there) the files.  To make it easy, add the windows disks to fstab (I do this in Fedora and it works great.  I assume that Ubuntu has the same/similar provision).

---

### Post by Maxzeroedge on 2011-06-05
I have 4 partitions on my PC and if I install ubuntu on one of them (Windows installed separately on aeparate partition), can I access the files in the other two partitions and can I write to them?
Say I have
Windows 7 C: NTFS
Ubuntu D:
My Stuffs E:, F: NTFS

So can I read and write in E: and F:?

---

### Post by webofunni on 2011-06-06
From Ubuntu, Yes. From Windows you need third party tools to access ext file system.

---

