---
title: "No permissions to read data from DVD"
date: 2009-11-28
forum: General Help
---

### Post by Scyron on 2009-11-28
I have a (real) copy of Medieval II: Total War and was trying to install it on Karmic. When I inserted the second DVD, it mounted to /media/MED2TW_2... but no data could be read from it. I opened the path in nautilus it appeared to empty; the output of ls in /media/MED2TW_2 looks like the following.

```

ls: cannot access directx9: Permission denied
........
ls: cannot access setup.isn: Permission denied
00000001.TMP  data2.cab    launcher    main        setup.exe  setup.isn
Autorun.inf   directx9     Launch.exe  SECDRV.SYS  setup.ico
data1.cab     DrvMgt.dll   Launch.ini  Setup.bmp   setup.ini
data1.hdr     ISSetup.dll  layout.bin  _setup.dll  setup.inx

```

I tried running sudo chmod 777 *, but this happens:

```

chmod: cannot access «00000001.TMP»: Permission denied
.......
chmod: cannot access «setup.isn»: Permission denied

```

In the permission tab of the DVD icon on the desktop, it claims the permissions of the disk cannot be determined.

Would anyone know how to force the permissions to let me access data on the disk? Sudo doesn't seem to work in this case.

---

### Post by Scyron on 2009-11-28
Bump.

---

### Post by DasEi on 2009-11-28
check out where dvd is mountes, /dev/cdrom0  or sth,  then

sudo chown -R RegularUsernameHere /dev/cdrom ,change username and mountpoint accordingly (mount tells you mountpoint)

---

### Post by Scyron on 2009-11-28
When I try chowning the mount point I get this:

```

chown: cannot access «/media/MED2TW_2/directx9»: Permission denied
..........
chown: cannot access «/media/MED2TW_2/setup.isn»: Permission denied
chown: changing property of «/media/MED2TW_2»: Read-only system

```

Note, I am using sudo here. It's pretty bizarre.

---

