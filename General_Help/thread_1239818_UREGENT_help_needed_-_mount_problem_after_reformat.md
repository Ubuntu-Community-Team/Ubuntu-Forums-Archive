---
title: "UREGENT help needed - mount problem after reformat!"
date: 2009-08-13
forum: General Help
---

### Post by Thanh-BKK on 2009-08-13
(SOLVED)

Hello.

So i have just reformatted one of my NTFS partitions to ext3 and now the damn thing won't mount. It says i don't have the necessary privileges!

This is my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=50c08996-facc-4c92-928e-82a2baa4bedc / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=9a5687d4-3ba5-4c6d-aba4-1d9bcb68f42b /home ext3 relatime 0 2
# Entry for /dev/sda5 :
UUID=14926b8f-7a88-4b5a-add9-80adca4d0280 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb5 /media/U-Torrent ntfs-3G defaults,locale=en_US.UTF-8 0 0
/dev/sdb3 /media/Backup ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb2 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Data ntfs-3g defaults,locale=en_US.UTF-8 0 0

The volume in question is /dev/sdb5. I have changed it to ext3 and all went fine, it mounts from within Gparted but it won't mount on boot nor manually without Gparted (sudo??)

I need this to mount when the machine boots as this is my torrent drive/partition. 

Please help me, i am completely lost here. Thanks in advance.

Thanh

---

### Post by Ocxic on 2009-08-14
change /dev/sdb5 /media/U-Torrent ntfs-3G defaults,locale=en_US.UTF-8 0 0
to
/dev/sdb5 /media/U-Torrent ext3 defaults 0 0

then "sudo mount -a"

---

### Post by Thanh-BKK on 2009-08-14
Hi.

Thank you very much. I tried that (among a million other things during a loooong googling session) and that didn't work. In the end i put something there that includes "relatime" instead of "defaults" as with "defaults" it didn't want to go.

Problem is solved now.... i had to change ownership of both actual volume (/dev/sdb5) as well as mount point (/media/U-Torrent) AND manually re-label the "125 GB Volume" to "U-Torrent" which is not exactly clearly visible how to do it - error message stating "not supported by backend" or some such.

Aaargh i thought honestly that Ubuntu (or Linux as such) would be smart enough to automatically do all that... as all i wanted was to change from NTFS to ext3. I had no idea that i would have to mess around with the ownership, all sorts of privileges and quite some command line hacking after the simple Gparted-task. 

Now i have another issue but that is for a new thread.

Kind regards.....

Thanh

---

