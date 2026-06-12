---
title: "How to make a proper dvd?"
date: 2006-05-14
forum: General Help
---

### Post by foxy123 on 2006-05-14
I've got a DVD which is not properly done. It has all the necessary files but it is not recognised by players.

```
:/media/cdrom0/VIDEO_TS# ls
VIDEO_TS.BUP  VTS_01_0.BUP  VTS_01_1.VOB  VTS_01_4.VOB  VTS_02_0.IFO
VIDEO_TS.IFO  VTS_01_0.IFO  VTS_01_2.VOB  VTS_01_5.VOB  VTS_02_1.VOB
VIDEO_TS.VOB  VTS_01_0.VOB  VTS_01_3.VOB  VTS_02_0.BUP

```

how can I re-burn it properly so I could watch it on a ordinary DVD player?

---

### Post by xurizaemon on 2006-05-23
first copy your original & badly burned DVD to HD (if you have two dvd readers you can skip this and copy direct of course ...)
```
cp -av /media/cdrom0/VIDEO_TS /tmp/dvd_dir
```
next part you need the growisofs package for, so first you may need to do
```
sudo apt-get -uf install growisofs
```
once that is installed, you can try burning it directly to DVD using ...
```
sudo growisofs -dvd-compat  -dvd-video -Z /dev/dvd /tmp/dvd_dir
```

we've just successfully burned an exported DVD Studio Pro project (dumps a VIDEO_TS and AUDIO_TS folder to disk) and it plays fine ... in the DVD player app on my laptop anyway. detects as a dvd and all ... cool!

good luck

---

