---
title: "5min to boot up"
date: 2009-10-30
forum: General Help
---

### Post by creed50 on 2009-10-30
hi

I made clean install for 9.10 ubuntu, but when i boot up my comp nothing happens for about 5min then it starts to boot up. With ubuntu 9.04 i had zero problems. By the way im installing 64bit version on AMD dual athlon


pleas help

---

### Post by P4man on 2009-10-30
have a look in dmesg (post its output)
If that doesnt reveal anything try installing [bootchart]("https://wiki.ubuntu.com/BootCharting")

That said, is it possible it was simply checking some disks?

---

### Post by creed50 on 2009-10-30
that's my bootchart

---

### Post by P4man on 2009-10-30
Impossible to read that, the image is resized.

---

### Post by creed50 on 2009-10-30
how about now



[https://wiki.ubuntu.com/BootCharting?action=AttachFile&do=view&target=urox-desktop-karmic-20091030-1.png](https://wiki.ubuntu.com/BootCharting?action=AttachFile&do=view&target=urox-desktop-karmic-20091030-1.png)

---

### Post by P4man on 2009-10-30
thats better. usplash is hogging your cpu for some reason it seems.
can you run

```
dmesg > dmesg.txt
```

in terminal and attach the file dmesg.txt (which will be made in your home folder) here ?

---

### Post by creed50 on 2009-10-30
here's mine  dmesg  [http://www.2shared.com/file/8774002/d64e6b93/dmesg.html](http://www.2shared.com/file/8774002/d64e6b93/dmesg.html)

---

### Post by creed50 on 2009-10-30
Is something wrong with my BIOS

---

### Post by P4man on 2009-10-30
> **creed50 said:**
> Is something wrong with my BIOS

Not that I can see, what makes you think that?
It rather looks like a problem with one of your disks, but im not sure. anyone else reading this but too lazy to download the dmesg, this is the relevant part:

```
[    6.804707] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.804795] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    6.804879] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    6.804964] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    6.814980] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.816728] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    6.822883] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    6.830998] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   90.416248] PM: Starting manual resume from disk
[   90.416253] PM: Resume from partition 8:5
[   90.416255] PM: Checking hibernation image.
[   90.416388] PM: Resume from disk failed.
[   90.438438] kjournald starting.  Commit interval 5 seconds
[   90.438450] EXT3-fs: mounted filesystem with writeback data mode.
```

---

### Post by creed50 on 2009-10-30
I have enough. I was using ubuntu for past 3 years now and it was working like a charm. But now come this Koala and f.... everything up. It's worst than Windows.

---

