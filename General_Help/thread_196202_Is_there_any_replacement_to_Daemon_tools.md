---
title: "Is there any replacement to Daemon tools?"
date: 2006-06-13
forum: General Help
---

### Post by eighthate on 2006-06-13
Is there any alternative for Daemon Tools(WIN) for Linux?

kk thx

---

### Post by eqisow on 2006-06-13
At the command line:

```
sudo mount -o loop filename.iso /media/cdrom0
```

Just be sure you don't have a CD-ROM mounted at the time. If you don't want it to interfere with your normal CD-ROM drives you can make a directory just for ISOs witht he following:

```
sudo mkdir /media/iso
```

Then you would mount with:

```
sudo mount -o loop filename.iso /media/iso
```

Edit: The mounted iso won't autorun or anything like a normal CD, but you can still navigate to the directory and run things as if it was a CD.

---

### Post by mlind on 2006-06-13
loopback device works atleast for .iso and .mdf images.
for .cue/.bin support you can use [cdemu]("http://cdemu.sourceforge.net/") or conversion utils like bchunk.

---

