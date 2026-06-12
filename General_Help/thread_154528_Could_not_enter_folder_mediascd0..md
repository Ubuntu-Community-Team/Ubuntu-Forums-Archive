---
title: "Could not enter folder /media/scd0."
date: 2006-04-03
forum: General Help
---

### Post by joey111 on 2006-04-03
hi, i get the message *Could not enter folder /media/scd0.*out of a sudden, when i want to watch a dvd. ownership of the file is root. 
the relevant line of my /etc/fstab is 
[I]/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/I], the mount command would be mount /dev/scd0 /media/scd0, but then it returns [I]mount: No medium found
[/I].
Why it doesnt work? in the past it did and in win xp it works too.

---

### Post by taurus on 2006-04-03
Instead of using /media/scd0, why not try /media/cdrom0?
```

xine dvd:/media/cdrom0
-or even-
xine dvd:/dev/hdc

```

---

### Post by joey111 on 2006-04-03
it doesnt work out, only the drive spins like mad;
i even edited the fstab to mount /dev/scd0 /media/cdrom;
thats my output now:[I]usr@fluffy:~$ vlc dvd:/media/scd0
VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/johannes/.dvdnav/.map'
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdread: Can't open file VIDEO_TS.IFO.
[00000261] main playlist: playlist is empty
[/I]
with the cdrom0 its the same exactly:[I]@fluffy:~$ vlc dvd:/media/cdrom0
VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
NAME OPEN FAILED
libdvdnav: Unable to find map file '/home/johannes/.dvdnav/.map'
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdread: Can't open file VIDEO_TS.IFO.
[I]
usr@fluffy:~$ vlc dvd:/media/cdrom0
VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
NAME OPEN FAILED
libdvdnav: Unable to find map file '/home/johannes/.dvdnav/.map'
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdread: Can't open file VIDEO_TS.IFO.
[00000261] main playlist: playlist is empty

[/I]
or i get: 
/media/cdrom0 is a folder, but a file was expected.

---

