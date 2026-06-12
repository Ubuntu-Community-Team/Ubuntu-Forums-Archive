---
title: "Re-installing Windows on Duel Boot"
date: 2006-04-27
forum: General Help
---

### Post by wizzkid on 2006-04-27
guys, my windows partition was messed up by virus. I want to re-format the partition containing the windows, but Im afraid it might delete the grub boot menu. Is there a way I can format the windows partition and maintain the grub boot menu?

Please help! :)

Here's my fstab for reference:
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc                proc     defaults 0 0
/dev/hda2       /                      reiserfs notail,atime,auto,rw,dev,exec,suid,nous                   er 0 1
/dev/hda3       /home              reiserfs defaults,atime,auto,rw,dev,exec,suid,no                   user 0 2
/dev/hda1       /media/hda1     ntfs     defaults,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda5       /media/Data     vfat     iocharset=utf8,umask=000   0       0
/dev/hda6       none                  swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by gingermark on 2006-04-27
Windows will destroy GRUB, cos it's like that.
But aftwards, use your install CD, and skip to the partioning bit. Obviously don't partition anything, but you should be able to mount your drives as you had them before there.

Then skip the end, and the installer should reinstall Grub.

I should say I have never tested this method (I have never needed to), but it is my understanding that it is supposed to work. Good luck.

EDIT: You can also have GRUB on a floppy disk, but I'm not sure how to do that. Might be worth looking into though.

---

### Post by Prospero2006 on 2006-04-27
I agree:

When you install windows, it will wipe grub off the map and you will be kicked directly to windows. Using a kubuntu installation c.d. it should be pretty simple to reinstall grub from that point. You can also try lilo, which is pretty easy to configure I think. If it were me, I'd do it like this:

      -Make sure all important information is backed up.
      -Format install windows.
      -grind coffee
      -boil water
      -pour gently into a thermos that will keep it hot for at least 5 hours.
      -Begin surgery on the mbr.

You'll figure it out. 
Pros

---

### Post by Sef on 2006-04-27
> Is there a way I can format the windows partition and maintain the grub boot menu?

No, but you can use the rescue (or restore) on the install disk to reinstall grub.

---

### Post by wizzkid on 2006-04-28
thanks guys.. :) correct, it should have coffee... I love coffee :) will try it out.. thanks a lot :)

---

### Post by wizzkid on 2006-04-28
Thanks guys.. I have successfuly restore the grub :) i just install the grub boot loader on the MBR :)

Thanks a lot :)

---

