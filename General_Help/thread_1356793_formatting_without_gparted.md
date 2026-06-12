---
title: "formatting without gparted"
date: 2009-12-16
forum: General Help
---

### Post by Gizenshya on 2009-12-16
(background) I'm trying to [convert a WUBI installation to "full," but I ran into a slew of problems.  ATM, I'm stuck [url=http://ubuntuforums.org/showthread.php?t=1356037]with a uuid lib problem](http://ubuntuforums.org/showthread.php?t=1354287) that is keeping me from installing gparted.  Without partitioning my destination drive, I cannot copy my wubi to a new drive.

(question) Is there any way to format without gparted?  Or is there any partitioning (deb package) software available that doesn't require the "uuid lib" that I'm having problems with?  I can't do the sudo apt-get, as the ubuntu box is not connected to the internet.  It goes from this win box to an SD card to the ubuntu box.

If not, can someone help me get the lib uuid problem resolved from that second link?

---

### Post by zkriesse on 2009-12-16
> **Gizenshya said:**
> (background) I'm trying to [http://ubuntuforums.org/showthread.php?t=1354287](http://ubuntuforums.org/showthread.php?t=1354287) convert a WUBI installation to "full," but I ran into a slew of problems.  ATM, I'm stuck [with a uuid lib problem]("http://ubuntuforums.org/showthread.php?t=1356037") that is keeping me from installing gparted.  Without partitioning my destination drive, I cannot copy my wubi to a new drive.

(question) Is there any way to format without gparted?  Or is there any partitioning (deb package) software available that doesn't require the "uuid lib" that I'm having problems with?  I can't do the sudo apt-get, as the ubuntu box is not connected to the internet.  It goes from this win box to an SD card to the ubuntu box.

If not, can someone help me get the lib uuid problem resolved from that second link?

I believe you can use the Ubuntu Live CD or burn a Gparted CD and then stick it in the system and use it that way...I'm not completely positive therefore I shall research it....

---

### Post by SuperSonic4 on 2009-12-16
You can use cfdisk to make partitions and the mk... to make them. For example making sda2 into ext4:

```
sudo cfdisk /dev/sda
```

cfdisk is self-explanatory IMO

```
sudo mkfs.ext4 /dev/sda2
```

Swap /dev/sda2 for whatever partition you use



Also live CDs have gparted on, if you're on windows you can download the ISO and burn it to cd using infrarecorder or another burner

---

