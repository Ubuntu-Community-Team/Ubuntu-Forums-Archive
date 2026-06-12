---
title: "mounting an image"
date: 2006-06-16
forum: General Help
---

### Post by geearf on 2006-06-16
Hello,

I have some problem mounting an cd-rom image file.
I tried with mount -o loop but it says it does not know the filesystem.
I tried with cdemu which tells me that there is a problem with devfs.
I just tried with kiso, which tells me like mount -o loop.

I tried it under windows with nero image drive and I had no problem at all.
A file here only tells me it's a data file.

Thanks for any help.

---

### Post by BitTorrentBuddha on 2006-06-16
Are you using the word "loop" in the command, it should look like this, without loop:```
mount -o /path/to/image.iso /path/to/mountpoint
```

---

### Post by geearf on 2006-06-16
Hello,

yes I was using the word loop, but even without it I got : 

mount: can't find /mnt/iso in /etc/fstab or /etc/mtab

So then I tried with the folder used for my second DVD-player, I got :

mount: No medium found

Then I added /mnt/iso to the fstab and got :

wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

(this is the same message I used to get).

I don't really know what's wrong, I have a feeling the problem comes from the image though.

---

### Post by ifokkema on 2006-06-16
[QUOTE=geearf]I don't really know what's wrong, I have a feeling the problem comes from the image though.[/QUOTE]

Yup, this is not a ISO 9660 image. It's probably some Nero specific image, or something. The file command output should be:

```
filename.iso: ISO 9660 CD-ROM filesystem data
```

---

### Post by geearf on 2006-06-16
Alright I'll try to see that with some windows apps (maybe through wine).

Thanks.

---

### Post by geearf on 2006-06-16
I converted the file under Windows, and now I have no problem.

Thanks for your help :)

---

