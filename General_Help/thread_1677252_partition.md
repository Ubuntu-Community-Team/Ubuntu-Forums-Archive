---
title: "partition?"
date: 2011-01-28
forum: General Help
---

### Post by Crux_Dissimilata on 2011-01-28
Is there a way that I can split up my HD so there is a part that can not be affected by Ubuntu to store my files etc.. If something goes wrong then and I would need to re-install Ubuntu I at least have all my data stored in a safe location.

---

### Post by Bucky Ball on 2011-01-28
[http://au.altavista.com/web/results?fr=altavista&itag=ody&q=partition+a+hard+drive+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?fr=altavista&itag=ody&q=partition+a+hard+drive+ubuntu&kgs=0&kls=0)

Please, let your fingers do the walking before posting. Cheers. ;)

---

### Post by dino99 on 2011-01-28
/home is the partition to store the data in a safe way. here is a howto to prepare installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by srs5694 on 2011-01-28
> **Crux_Dissimilata said:**
> Is there a way that I can split up my HD so there is a part that can not be affected by Ubuntu to store my files etc.. If something goes wrong then and I would need to re-install Ubuntu I at least have all my data stored in a safe location.

Chances are dino99's suggestion of using a separate /home partition is what you're after; however, your phrasing of the requirement as "so there is a part that can not be affected by Ubuntu" makes me wonder if you're talking about storing Linux files or storing non-Linux files. The trouble is that any partition used to store Linux files is by definition "affected by Ubuntu," so there's no way to be both useful from Ubuntu and immune to Ubuntu's influence. If you just mean that you want your user data files to be safe when re-installing Ubuntu or in case your Ubuntu installation gets badly corrupted, then a separate /home partition is the way to go, but of course Ubuntu controls and affects that partition.

If, however, you want to keep *Windows* data safe from any possible meddling by Ubuntu, the only *completely* safe solution is to use a separate physical disk that you can easily disconnect before booting Ubuntu. As an OS, Ubuntu will have access to all the hardware on the computer, and there are ways to completely trash a filesystem even if you don't normally use it from the OS that's running, so physically disconnecting the disk is the only way to keep its data completely isolated from Ubuntu. There is a middle ground, though: You can create an /etc/fstab file entry for the partition that keeps it from mounting automatically, as in:

```

/dev/sda2    /mnt/windows   ntfs-3g   noauto,ro    0 0

```

This entry tells Linux that /dev/sda2 is to be associated with /mnt/windows, that it's NTFS, that it should not be automatically mounted ("noauto"), and that if and when it is mounted, it should be mounted read-only ("ro"). When you reboot, the partition should not be auto-mounted and it will remain inaccessible unless you type "sudo mount /mnt/windows" (or various equivalent commands). This will protect the contents of /dev/sda2 from most casual meddling that could damage it; to do damage, you'd need to use root access (as via "sudo") to write directly to /dev/sda2 or to mount the partition using options that override those in /etc/fstab.

---

### Post by Crux_Dissimilata on 2011-01-29
I was hoping there was a way to split off a part of the HD that I am now using where I got Ubuntu installed to store videos and .pdf files.

I looked in to GParted but I am not sure if it is safe to unmount /dev/sda1 and steal 100 Gig from it to create a separate partition.

---

### Post by Megaptera on 2011-01-29
Hi crux,
You could have a separate partition as shown at link below. This talks about sharing docs etc between Windows and Ubuntu but you could just do the Ubuntu side of it:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

