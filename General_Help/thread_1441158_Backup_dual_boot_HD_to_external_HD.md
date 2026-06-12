---
title: "Backup dual boot HD to external HD"
date: 2010-03-28
forum: General Help
---

### Post by Ncshipman on 2010-03-28
Hi,

I am dual booting windows and ubuntu.  I bought a external hard drive to use as a backup solution.  I like the idea of my external HD being an exact copy of my internal one so that if my internal one completely fails I can just plug my external one in and carry on (it's an internal drive in an enclosure).

I notice a lot of people use rsync to backup their home directory.  Can I use rsync (or something else) to back up the whole drive including the Windows partition.

Thanks,
Nick

---

### Post by MichaelSammels on 2010-03-28
I think so. DD would also work, but if you want to try rysnc:

```
rsync -arHx src dest
```

So if you source is / and your desitnation is your external it would be something like:

```
rsync -arHx / /mnt/external
```

---

### Post by oldfred on 2010-03-28
I do not have an answer to your question but want to point out some issues.

If you do a full mirror copy which you can do with several tools, you have to copy the UUIDs which are unique partition identifiers. Your grub and fstab have these settings to know what partition to boot from. If you do the full copy and have the external plugged in it may boot that copy randomly as the identical UUIDs do not let the system know what to uniquely boot. If you do not do a full copy then the UUIDs will be different and the grub and fstab that you copy will not let you boot.

I have three internal drives but have four operating systems installed. Win, old jaunty, current karmic and lucid beta with each drive having a different bootable drive. All my data is in separate partitions that I do backup (not as often as I should- do as I say do not do as I do;)).

I would think about a separate install on the external and copy /home and or any data partitions. Also export a list of all your installed applications regularly so it gets backed up. Some make a lot of system settings so recommend backing up /etc - I try to keep track of changes and only copy those I have changed, but I have my old install to go back to just in case.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

sudo cp /etc/apt/sources.list ~/sources.list.backup
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by Ncshipman on 2010-03-28
Thanks guys :-)

@ oldfred:  Yeh I think that UUID thing might explain some problems I was having earlier.  I can't easily reinstall windows as I no longer have disc but would reinstalling ubuntu on the other hard disk stop any problems whilst using ubuntu?

---

### Post by oldfred on 2010-03-28
There should be no major issues with installing Ubuntu on the external. I have seen where users installed to the external and it put its grub on the internal, but sure to use the advanced button on the partition setup final screen ( i missed it on my first install of lucid, screen 9) so you can be sure grub is installed to the external.

---

### Post by Ncshipman on 2010-03-28
cool thanks for the info.

---

