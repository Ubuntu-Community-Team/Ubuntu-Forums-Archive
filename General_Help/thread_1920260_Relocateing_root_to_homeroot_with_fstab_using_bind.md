---
title: "Relocateing /root/ to /home/root/ with fstab using bind"
date: 2012-02-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-02-04
i would like to relocate my /root folder to /home/root so it will be on a different partition and more importantly on a hdd and not on a ssd i know i could jsut mount it in it's own partition but i would rather not use that method since the number of partitions is limited by the partition table

i know i need to copy my /root to /home/root but what needs to go in fstab?

---

### Post by xyzzyman on 2012-02-04
As you don't log into root on Ubuntu, why do you want to relocate it? There should be almost nothing in that directory. You probably don't want /root on another partition from / as there's a number of circumstances where that could break recovery mode I think.

---

### Post by pqwoerituytrueiwoq on 2012-02-04
cache files from using gksu nautilus and some lock files it is to lower the wear on my ssd which i need to rma it failed after 80 power on days
i dont need to log into root

---

### Post by llamabr on 2012-02-04
In ubuntu, I can't think of any good reason to do this, as a few bad ones.  Why do you want it on its own partition?  Probably there's nothing in there, anyway.

---

### Post by xyzzyman on 2012-02-04
fstab is to mount a partition to a folder, so that's not possible. maybe you make a /home/root directory, copy everything, and then symlink it? You're going to regret this at some point. How often are you in nautilus in sudo?

---

### Post by pqwoerituytrueiwoq on 2012-02-04
> **llamabr said:**
>   Probably there's nothing in there, anyway.
[FONT=Courier New]sudo tree -a /root/[/FONT]
```
/root/
|-- .aptitude
|   `-- config
|-- .bash_history
|-- .bashrc
|-- .config
|   |-- bleachbit
|   |   `-- bleachbit.ini
|   |-- enchant
|   |   |-- en_US.dic
|   |   `-- en_US.exc
|   |-- geany
|   |   |-- colorschemes
|   |   |-- filedefs
|   |   |   `-- filetypes.README
|   |   |-- geany.conf
|   |   |-- tags
|   |   `-- templates
|   |       |-- files
|   |       `-- templates.README
|   |-- Google
|   |   `-- GoogleEarthPlus.conf
|   |-- gtk-2.0
|   |   `-- gtkfilechooser.ini
|   `-- Trolltech.conf
|-- .dbus
|   `-- session-bus
|       `-- 341decd8bef4285bdd4e51d74e089cb5-0
|-- .debtags
|-- Desktop
|-- .esd_auth
|-- .gconf
|   `-- apps
|       |-- file-roller
|       |   |-- dialogs
|       |   |   |-- batch-add
|       |   |   |   `-- %gconf.xml
|       |   |   `-- %gconf.xml
|       |   |-- %gconf.xml
|       |   |-- general
|       |   |   `-- %gconf.xml
|       |   |-- listing
|       |   |   `-- %gconf.xml
|       |   `-- ui
|       |       `-- %gconf.xml
|       |-- gconf-editor
|       |   `-- %gconf.xml
|       |-- %gconf.xml
|       |-- gedit-2
|       |   |-- %gconf.xml
|       |   |-- plugins
|       |   |   |-- filebrowser
|       |   |   |   |-- %gconf.xml
|       |   |   |   `-- on_load
|       |   |   |       `-- %gconf.xml
|       |   |   `-- %gconf.xml
|       |   `-- preferences
|       |       |-- editor
|       |       |   |-- auto_indent
|       |       |   |   `-- %gconf.xml
|       |       |   |-- bracket_matching
|       |       |   |   `-- %gconf.xml
|       |       |   |-- colors
|       |       |   |   `-- %gconf.xml
|       |       |   |-- current_line
|       |       |   |   `-- %gconf.xml
|       |       |   |-- %gconf.xml
|       |       |   |-- line_numbers
|       |       |   |   `-- %gconf.xml
|       |       |   |-- right_margin
|       |       |   |   `-- %gconf.xml
|       |       |   `-- wrap_mode
|       |       |       `-- %gconf.xml
|       |       |-- %gconf.xml
|       |       `-- ui
|       |           |-- %gconf.xml
|       |           `-- statusbar
|       |               `-- %gconf.xml
|       |-- gnome-power-manager
|       |   |-- buttons
|       |   |   `-- %gconf.xml
|       |   `-- %gconf.xml
|       |-- gnome-settings
|       |   |-- %gconf.xml
|       |   `-- gedit
|       |       `-- %gconf.xml
|       |-- indicator-session
|       |   `-- %gconf.xml
|       |-- metacity
|       |   |-- %gconf.xml
|       |   `-- general
|       |       `-- %gconf.xml
|       `-- nautilus
|           |-- %gconf.xml
|           `-- preferences
|               `-- %gconf.xml
|-- .gconfd
|   `-- saved_state
|-- .gnome2
|   |-- accels
|   |   |-- gconf-editor
|   |   |-- gedit
|   |   `-- nautilus
|   |-- file-roller
|   |-- gedit
|   |   `-- gedit-2
|   `-- nautilus-scripts
|-- .gnome2_private
|-- .googleearth
|   |-- Cache
|   |   |-- dbCache.dat
|   |   |-- dbCache.dat.index
|   |   `-- dbroot_cache
|   |-- crashlogs
|   |   `-- crashlog-4e0dc4e9.txt
|   `-- instance-running-lock -> /proc/2575
|-- .gstreamer-0.10
|   `-- registry.x86_64.bin
|-- .gtk-bookmarks
|-- .local
|   `-- share
|       |-- .converted-launchers
|       `-- vino
|-- .nautilus
|-- .nvidia-settings-rc
|-- .profile
|-- .pulse
|   `-- 341decd8bef4285bdd4e51d74e089cb5-runtime -> /tmp/pulse-2L9K88eMlGn7
|-- .pulse-cookie
|-- .recently-used.xbel
|-- .ssh
|   `-- known_hosts
|-- .synaptic
|   |-- lock
|   |-- lock.non-interactive
|   |-- log
|   |   |-- 2011-06-27.112917.log
|   |   |-- 2011-06-27.121739.log
|   |   |-- 2011-06-27.122016.log
|   |   |-- 2011-06-27.123149.log
|   |   |-- 2011-06-27.123214.log
|   |   |-- 2011-06-27.124422.log
|   |   |-- 2011-06-27.133100.log
|   |   |-- 2011-06-27.153606.log
|   |   |-- 2011-06-27.153626.log
|   |   |-- 2011-06-29.121437.log
|   |   |-- 2011-06-29.164612.log
|   |   |-- 2011-06-29.164645.log
|   |   |-- 2011-06-29.170419.log
|   |   |-- 2011-06-30.162855.log
|   |   |-- 2011-07-03.165312.log
|   |   |-- 2011-07-06.083406.log
|   |   |-- 2011-07-06.102948.log
|   |   |-- 2011-07-07.173555.log
|   |   |-- 2011-07-11.085426.log
|   |   |-- 2011-07-11.094332.log
|   |   |-- 2011-07-12.205808.log
|   |   |-- 2011-07-15.092403.log
|   |   |-- 2011-07-15.213640.log
|   |   |-- 2011-07-16.102056.log
|   |   |-- 2011-07-17.092823.log
|   |   |-- 2011-07-19.093214.log
|   |   |-- 2011-07-22.084815.log
|   |   |-- 2011-07-26.090124.log
|   |   |-- 2011-07-27.081343.log
|   |   |-- 2011-07-28.081642.log
|   |   |-- 2011-07-29.091020.log
|   |   |-- 2011-08-02.092909.log
|   |   |-- 2011-08-03.104844.log
|   |   |-- 2011-08-05.191406.log
|   |   |-- 2011-08-07.085935.log
|   |   |-- 2011-08-09.091144.log
|   |   |-- 2011-08-09.140530.log
|   |   |-- 2011-08-09.191919.log
|   |   |-- 2011-08-15.102655.log
|   |   |-- 2011-08-16.012951.log
|   |   |-- 2011-08-16.131759.log
|   |   |-- 2011-08-16.132754.log
|   |   |-- 2011-08-16.163057.log
|   |   |-- 2011-08-17.214319.log
|   |   |-- 2011-08-18.195043.log
|   |   |-- 2011-08-18.195234.log
|   |   |-- 2011-08-18.200017.log
|   |   |-- 2011-08-19.085535.log
|   |   |-- 2011-08-19.090537.log
|   |   |-- 2011-08-19.092145.log
|   |   |-- 2011-08-19.094301.log
|   |   |-- 2011-08-19.234319.log
|   |   |-- 2011-08-19.234412.log
|   |   |-- 2011-08-20.032238.log
|   |   |-- 2011-08-20.174906.log
|   |   |-- 2011-08-21.163431.log
|   |   |-- 2011-08-21.171301.log
|   |   |-- 2011-08-21.223521.log
|   |   |-- 2011-08-23.104211.log
|   |   |-- 2011-08-31.084319.log
|   |   |-- 2011-09-01.105207.log
|   |   |-- 2011-09-01.105504.log
|   |   |-- 2011-09-02.100329.log
|   |   |-- 2011-09-06.204045.log
|   |   |-- 2011-09-06.205459.log
|   |   |-- 2011-09-08.150209.log
|   |   |-- 2011-09-09.103727.log
|   |   |-- 2011-09-09.124321.log
|   |   |-- 2011-09-14.080747.log
|   |   |-- 2011-09-15.202150.log
|   |   |-- 2011-09-20.095614.log
|   |   |-- 2011-09-21.093309.log
|   |   |-- 2011-09-23.181624.log
|   |   |-- 2011-09-27.151758.log
|   |   |-- 2011-09-28.135632.log
|   |   |-- 2011-09-29.093518.log
|   |   |-- 2011-10-05.110150.log
|   |   |-- 2011-10-11.113025.log
|   |   |-- 2011-10-13.103817.log
|   |   |-- 2011-10-17.141501.log
|   |   |-- 2011-10-18.180705.log
|   |   |-- 2011-10-19.102228.log
|   |   |-- 2011-10-20.092036.log
|   |   |-- 2011-10-22.144302.log
|   |   |-- 2011-10-25.090446.log
|   |   |-- 2011-10-26.104007.log
|   |   |-- 2011-10-29.094752.log
|   |   |-- 2011-10-30.202308.log
|   |   |-- 2011-11-11.094655.log
|   |   |-- 2011-11-15.114829.log
|   |   |-- 2011-11-15.120210.log
|   |   |-- 2011-11-16.093751.log
|   |   |-- 2011-11-17.121811.log
|   |   |-- 2011-11-18.092746.log
|   |   |-- 2011-11-19.155410.log
|   |   |-- 2011-11-23.184944.log
|   |   |-- 2011-11-24.172756.log
|   |   |-- 2011-11-28.121840.log
|   |   |-- 2011-11-30.111857.log
|   |   |-- 2011-12-02.064223.log
|   |   |-- 2011-12-03.024418.log
|   |   |-- 2011-12-03.024536.log
|   |   |-- 2011-12-05.094428.log
|   |   |-- 2011-12-06.180843.log
|   |   |-- 2011-12-09.091319.log
|   |   |-- 2011-12-15.083302.log
|   |   |-- 2011-12-16.094410.log
|   |   |-- 2011-12-17.091807.log
|   |   |-- 2011-12-19.124707.log
|   |   |-- 2011-12-20.100438.log
|   |   |-- 2011-12-21.083112.log
|   |   |-- 2011-12-22.140632.log
|   |   |-- 2011-12-31.211545.log
|   |   |-- 2012-01-05.082950.log
|   |   |-- 2012-01-06.095703.log
|   |   |-- 2012-01-14.202916.log
|   |   |-- 2012-01-15.140815.log
|   |   |-- 2012-01-15.143752.log
|   |   |-- 2012-01-16.131457.log
|   |   |-- 2012-01-16.173750.log
|   |   |-- 2012-01-20.082830.log
|   |   |-- 2012-02-04.121128.log
|   |   `-- 2012-02-04.121243.log
|   |-- options
|   |-- selections.proceed
|   |-- synaptic.conf
|   `-- tmp
|-- .thumbnails
|   |-- fail
|   |   `-- gnome-thumbnail-factory
|   |       `-- e8dabc5e61008486dd16d59f3e02c6e0.png
|   `-- normal
|       |-- 363053300dcb78e2cbc5226652bb7fa4.png
|       `-- 6056a7932259df097538a1b3b914f733.png
`-- .wapi

74 directories, 196 files

```

edit: i think this is what i want in fstab
/home/root /root bind defaults,bind 0 0

---

### Post by pqwoerituytrueiwoq on 2012-02-04
that was it :)
[FONT=Courier New][SIZE=3]/home/root /root bind defaults,bind 0 0[/SIZE][/FONT]
of course I moved the files there before mounting it from a live usb stick
1) mkdir /home/root
2) boot live usb or cd
3) move /root/* to /home/root/
4) make permissions on /home/root match /root
5) update fstab
6) reboot

---

### Post by xyzzyman on 2012-02-05
Is your /tmp directory already off the ssd? That /root is being so infrequently that it's essentially zero. Your /tmp on the other hand...

---

### Post by pqwoerituytrueiwoq on 2012-02-05
/tmp, /var, and /home are NOT on the ssd

---

### Post by xyzzyman on 2012-02-05
> **pqwoerituytrueiwoq said:**
> /tmp, /var, and /home are NOT on the ssd

If you have time for science, disconnect the HDD so only the SSD is installed, and try booting into recovery. I'm curious if it'll still work without the /root directory accessible or if it'll just use the old one.

---

### Post by pqwoerituytrueiwoq on 2012-02-05
here is my fstab only / is on a ssd
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation 
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    discard,errors=remount-ro,noatime,nodiratime 0       1
# /home was on /dev/sdb3 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults                             0       2
# /mnt/HardDisks was on /dev/sdb5 during installation
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /mnt/HardDisks  ext4    defaults                             0       2
# /mnt/DiskImages was on /dev/sdb6 during installation
UUID=89068a31-dc74-4dad-bf5f-8bfec96850de /mnt/DiskImages ext4    defaults                             0       2
# /var was on /dev/sdb2 during installation
UUID=5cae72de-be5c-4586-90ec-c65ce056555b /var            ext4    defaults                             0       2
# /tmp was made a ram disk after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777           0       0
# swap was on /dev/sdb4 during installation
UUID=047fac32-955c-4318-b70c-479c433a24a8 none            swap    sw                                   0       0

# move /root to /home/root to get it off the ssd
/home/root /root bind defaults,bind 0 0

```i am already on a backup hdd as it is due to the ssd failing which I am in the process of RMAing why don't you try it on a test system

---

