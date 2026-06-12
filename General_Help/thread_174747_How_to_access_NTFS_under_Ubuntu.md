---
title: "How to access NTFS under Ubuntu?"
date: 2006-05-12
forum: General Help
---

### Post by Zdravko on 2006-05-12
I have a dual boot PC with MS XP and Ubuntu installed. The problem is that under Ubuntu I have no access to the Windows partitions. Is there a way to gain at least read rights to these?
Best regards

---

### Post by dg_w on 2006-05-12
Ok as the partiton is NTFS you are going to get read only (unless you use fuse or something)

1. Create a directoy ie
sudo mkdir /windows
sudo chmod 777 /windows

2.
create a line in /etc/fstab
sudo gedit /etc/fstab
put in the following line
/dev/hda1   /windows   ntfs   user,fmask=0000,dmask=0000   0   0
(change /dev/hda1 to what ever partition you are trying to mount)
save

Should not mount when you start, with full permissions
To mount manualy
mount /windows


Hope that helps
dg_w

---

### Post by Zdravko on 2006-05-12
Nope, it doesn't help.
Here is fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde8       /home           ext3    defaults        0       2
/dev/hde1       /media/hde1     ntfs    defaults        0       0
/dev/hde5       /media/hde5     ntfs    defaults        0       0
/dev/hde6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /windows ntfs user,fmask=0000,dmask=0000 0 0

I added the last line, but while starting, Ubuntu matched it "FAIL".
Furthermore, my loading takes sooo much time. The initial graphical display with brown text dissapears and the ugly console appears to mount slower the devices. Under Windows I have 2 partitions. I actually need both for READ. But I think that during start, there are error messages concerning the other devices. What could it be the problem? On my desktop I have hde1 and hde5 - both without any access. Are these my windows partitions?

---

### Post by Omnios on 2006-05-12
Ubuntu wiki on mounting window partitions.
[http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")
There is also a real good link in my signature on fstab. Tuxfiles.

---

### Post by dg_w on 2006-05-12
Yes these are the partitions    So

Change
/dev/hde1 /media/hde1 ntfs defaults 0 0
/dev/hde5 /media/hde5 ntfs defaults 0 0

to read 

/dev/hde1 /media/hde1 ntfs user,fmask=0000,dmask=0000 0 0
/dev/hde5 /media/hde1 ntfs user,fmask=0000,dmask=0000 0 0

And remove the 
/dev/hde1 /media/hde1 ntfs user,fmask=0000,dmask=0000 0 0
line

---

### Post by dg_w on 2006-05-12
Ops my typo

I meant remove the 

/dev/hda1 /windows ntfs user,fmask=0000,dmask=0000 0 0

line 

Sorry ](*,)

---

### Post by Zdravko on 2006-05-12
[dg_w]("http://www.ubuntuforums.org/member.php?u=81071"), thanks! It worked. I only hope that mount-unmount operations won't harm the NTFS data :)

---

### Post by ZylGadis on 2006-05-12
Zdrasti Zdravko,
You won't harm your ntfs data as long as you **don't write to the NTFS partition**. Linux does not support writing to NTFS very well, and you are bound to have problems even if it works at first. You'd best it mount read-only.

---

### Post by Zdravko on 2006-05-12
[ZylGadis]("http://www.ubuntuforums.org/member.php?u=56653"), is the way I mounted it - Read-only? I guess - yes. I just copied several directories from NTFS to my home folder. That's all - everything else is untouched.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde8       /home           ext3    defaults        0       2
/dev/hde1 /media/hde1 ntfs user,fmask=0000,dmask=0000 0 0
/dev/hde5 /media/hde5 ntfs user,fmask=0000,dmask=0000 0 0
/dev/hde6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

