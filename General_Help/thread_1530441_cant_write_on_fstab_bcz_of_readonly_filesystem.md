---
title: "cant write on fstab bcz of readonly filesystem"
date: 2010-07-13
forum: General Help
---

### Post by muhammed irshad on 2010-07-13
[SIZE=4]i was using ubuntu 9.04 .
i had changed  fstab mount option of my ubuntu partition from exec,utf8 to executf8.now i cant get the gui of my ubuntu .

only command line appears and i cant edit fstab even from root.

it says that the filesystem is readonly.i tried  mount -o remount,rw
it does'nt work.if anyone have a methode other  than reinstall my ubuntu.
[/SIZE]

---

### Post by drs305 on 2010-07-13
If you have a LiveCD, boot to the Desktop. Open a terminal and then run the following. If your Ubuntu is not on sda1, change it to the proper partition.
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```

Make the changes, save the file, then unmount the partition and reboot:
```
sudo umount /dev/sda1
sudo reboot now
```

---

### Post by muhammed irshad on 2010-07-14
[SIZE=4]i did like you said.....still the problem exist....
[/SIZE]

---

### Post by muhammed irshad on 2010-07-14
[SIZE=4]I did edit the fstab like you said.my ubuntu was in  dev/sda6.
but after i reboot the following message displayed 
-[B]"could not start the X server(your graphical environment)
due to some internal error .please contact your system adminstator or  check your syslog to diagnose.In the meantime 
this display will be disabled.Please restart the GDM when the problem is  corrected-"[/B]
what i want to do to get my ubuntu back other than reinstalling.can you  please say why this happend.[/SIZE]

---

