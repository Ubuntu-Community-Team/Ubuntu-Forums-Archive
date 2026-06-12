---
title: "Unable to mount external drive"
date: 2011-07-29
forum: General Help
---

### Post by jocampo on 2011-07-29
Having issues while mounting my 1TB passport USB drive. When running this command....

```
sudo mount /dev/sdc /mnt/WD/
```

I got this error: mount: you must specify the filesystem type

I even tried adding the filesystem, which was or is ext4 ...

```
sudo mount -t ext4  /dev/sdc /mnt/WD/
```

Getting a different error instead: 


```
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Any ideas? I should mention that this was working just a few hours ago. There was a power glitch and my Ubuntu headless server lost power. I turned it on and since then, I am getting this error. I would prefer not to format via GUI .... 1st because I have data there , 2nd, because I don't want to rely on a graphical interface but being able to fix this via terminal.

Thanks in advance,

---

### Post by karlson on 2011-07-29
> **jocampo said:**
> Having issues while mounting my 1TB passport USB drive. When running this command....

```
sudo mount /dev/sdc /mnt/WD/
```

I got this error: mount: you must specify the filesystem type

I even tried adding the filesystem, which was or is ext4 ...

```
sudo mount -t ext4  /dev/sdc /mnt/WD/
```

Getting a different error instead: 


```
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


Have you tried
```

fsck -t ext4 /dev/sdc

```

---

### Post by jocampo on 2011-07-29
> **karlson said:**
> Have you tried
```

fsck -t ext4 /dev/sdc

```

No... I just did it ... fixed several inodes on the process ... but that was not a good idea, actually really stupid (talking about me, not your advice, so no offense), I lost all my data. But this is a external drive for backups, so not big deal.

Did not fix my issue and still would like to know why I was not able to mount the drive. I guess I will never know. This is the 2nd time this happened by the way. I had to format via GUI the 1st time and re-create the filesystem again.

---

### Post by redFlameStar on 2011-07-30
Just wondering what format is the external drive. If its exFAT you may need to install the support driver. That was the problem with one of mine.

---

### Post by garvinrick4 on 2011-07-30
sudo mkdir /mnt/WD
sudo mount /dev/[COLOR=Red]sdc1[/COLOR] /mnt/WD
#sudo fdisk -l (lower case L) for partition numbers.
##IF you want to mount in media so as to be on desktop must also mkdir and use partition number.

---

### Post by jocampo on 2011-07-30
Yeah, I created a folder via mdkir ... as I said, was working before..

I bought it here in USA at BestBuy. All my computers, except work, run Linux so I format using ext4. I was able to use it via cron for last 2 or 3 days. But I remember was facing the same issue 1st day I bought and after format via GUI. It looks like my Ubuntu headless does not like the GUID that is generated via GUI/Ubuntu.

Anyway, re-format again, via GUI (from my Ubuntu desktop) but I am using vfat this time I did not want to. I think this can create issues with large files, but not so sure. It is running the cron now and I was able to mount it this time.

---

### Post by garvinrick4 on 2011-07-30
> Anyway, re-format again, via GUI (from my Ubuntu desktop) but I am using vfat this time I did not want to.
Why not ext4 or NTFS instead of older Fat?
If you want to without grapical use your fdisk commands as per below:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by jocampo on 2011-07-30
> **garvinrick4 said:**
> Why not ext4 or NTFS instead of older Fat?
If you want to without grapical use your fdisk commands as per below:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Great question.

FAT will allow me to read and use it on my Mac Mini, Windows machine and Linux laptop. I believe Mac does not read ext4. I know for sure, Windows won't read ext4.

Anyway, I am re-running the job, again. After re-formatting using FAT I am getting some "chown" errors when using rsync. I believe is because the FAT format and permissions. I removed the "a" option and using zrv only ...

---

### Post by Mark Phelps on 2011-07-30
Did you happen to notice the details in the mount instructions?

Yours had a trailing slash "/"

The CORRECT ones did NOT.

That little difference is enough to cause the mount command to fail.

---

### Post by jocampo on 2011-07-30
Yeah, the device and mount point were right.

I think has something to do with the passport itself. I've read it has a weird internal partition and that acts erratically sometimes when mounted on Linux.

Anyway, I still don't know what happened. I am assuming that lost formatting after the power issue with the server, I was not at home and did not unmount properly. So I will mark the thread as solved.

Thanks all for the advices though! ;)

---

