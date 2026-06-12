---
title: "Firefox download"
date: 2011-10-14
forum: General Help
---

### Post by imu96 on 2011-10-14
I was trying to download a document from my school's website when I got the error

"/tmp could not be saved, because an unknown error occurred."

"Try saving to a different location."

I later tried downloading a screenlet and I again got the same error...

so.... how do i fix it

by the way i am using firefox and i keep getting this stupid error

---

### Post by ibutho on 2011-10-14
Do you have enough disk space in the location that you are trying to save the file?

---

### Post by lovinglinux on 2011-10-14
Open Firefox Preferences, select the *General* tab, then tick the option "*Always ask me where to save files*" in the *Download* section. See if that helps.

---

### Post by imu96 on 2011-10-14
@lovinglinux: it is already on that setting

@ibutho: i don't know.... how do i check?

---

### Post by ibutho on 2011-10-14
```
df -h
```
and
```
du -h
```

---

### Post by imu96 on 2011-10-14
```
Filesystem            Size  Used Avail Use% Mounted on
rootfs                 50G  4.1G   45G   9% /
udev                  933M     0  933M   0% /dev
tmpfs                 940M  416K  939M   1% /dev/shm
tmpfs                 940M  728K  939M   1% /run
/dev/mapper/vg_imu96-lv_root
                       50G  4.1G   45G   9% /
tmpfs                 940M     0  940M   0% /sys/fs/cgroup
tmpfs                 940M     0  940M   0% /media
/dev/sda1             485M   70M  390M  16% /boot
/dev/mapper/vg_imu96-lv_home
                      241G  2.6G  226G   2% /home
/dev/mapper/vg_imu96-lv_root
                       50G  4.1G   45G   9% /tmp
/dev/mapper/vg_imu96-lv_root
                       50G  4.1G   45G   9% /var/tmp
/dev/mapper/vg_imu96-lv_home
                      241G  2.6G  226G   2% /home
```

and```


4.0K    ./.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
48K    ./.libreoffice/3/user/extensions/shared/registry
64K    ./.libreoffice/3/user/extensions/shared
300K    ./.libreoffice/3/user/extensions
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/simpress/toolbar
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/simpress/menubar
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/simpress/statusbar
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/simpress/images/Bitmaps
8.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/simpress/images
24K    ./.libreoffice/3/user/config/soffice.cfg/modules/simpress
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/swriter/toolbar
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/swriter/menubar
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/swriter/statusbar
4.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/swriter/images/Bitmaps
8.0K    ./.libreoffice/3/user/config/soffice.cfg/modules/swriter/images
24K    ./.libreoffice/3/user/config/soffice.cfg/modules/swriter
52K    ./.libreoffice/3/user/config/soffice.cfg/modules
56K    ./.libreoffice/3/user/config/soffice.cfg
1.9M    ./.libreoffice/3/user/config
892K    ./.libreoffice/3/user/database/biblio
904K    ./.libreoffice/3/user/database
3.3M    ./.libreoffice/3/user
3.3M    ./.libreoffice/3
3.3M    ./.libreoffice
12K    ./.dbus/session-bus
16K    ./.dbus
4.0K    ./dwhelper
2.4G    .
```

respectively....

---

### Post by ibutho on 2011-10-14
I can't see any obvious signs of the disk being full. Try the suggestions [here]("http://kb.mozillazine.org/Unable_to_save_or_download_files").

---

### Post by imu96 on 2011-10-14
o.... wait.... i just restarted my computer instead of just putting it on hibernate and now it downloads just fine... that was wierd.... anyway.... thanks for your help.... sorry for wasting your time....

---

