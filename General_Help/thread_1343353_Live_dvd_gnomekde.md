---
title: "Live dvd gnome/kde"
date: 2009-12-01
forum: General Help
---

### Post by konnorrigby on 2009-12-01
I have been working on this for a wile It is a live dvd that can be able to boot up multiple distros, such as kde or gnome. These are all that i have so far. and i need a little help so...
(I started with linux mint gnome 7)
this is my folder tree
```

.../Linux Live cd
/BOOT
  +/isolinux
/GNOME
  +/.disk
  +/casper
  +/drivers
  +preseed
/KDE
  +/.disk
  +/casper
  +/drivers
  +preseed

```

my isolinux.cfg looks like this..
```


default vesamenu.c32
timeout 100

menu background splash.jpg
menu title Welcome to Linux Mint 7 Gloria
menu color border 0 #00eeeeee #00000000
menu color sel 7 #ffffffff #33eeeeee
menu color title 0 #ffeeeeee #00000000
menu color tabmsg 0 #ffeeeeee #00000000
menu color unsel 0 #ffeeeeee #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000
menu hidden
menu hiddenrow 7
label glive
  menu label Start Linux Mint Gnome
  kernel /GNOME/casper/vmlinuz
  append  file=/cdrom/GNOME/preseed/mint.seed boot=casper initrd=/GNOME/casper/initrd.gz quiet splash --
label klive
  menu label Start Linux Mint KDE
  kernel /KDE/casper/vmlinuz
  append  file=/cdrom/KDE/preseed/mintkde.seed boot=casper initrd=/KDE/casper/initrd.gz quiet splash --

```
I have all of the folders correct... but for some reason, when i try it in qemu it doesn't work... any suggestions?

---

