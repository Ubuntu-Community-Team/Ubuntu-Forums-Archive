---
title: "file permissions inconsistent"
date: 2009-08-11
forum: General Help
---

### Post by Gwendolin on 2009-08-11
Hello,

I'm trying to playback DVD from my cd-rom, have already installed              **libdvdcss2** package,
only thing now is that I have a weird permission problems on file cdrom0:

/media$ ls -l -h
total 2.0K
lrwxrwxrwx 1 root       root        6 2009-07-26 01:50 cdrom -> cdrom0
dr--r--r-- 3 4294967295 4294967295 88 2004-01-01 02:00 cdrom0

and looking at the permissions attribute of cdrom0 "they are inconsistent..."

can't chmod it since it is a read-only file system.
can I remount it or something of the sort?

Thanks!

---

### Post by aesis05401 on 2009-08-11
> **Gwendolin said:**
> 
*snip*
```

/media$ ls -l -h
total 2.0K
lrwxrwxrwx 1 root       root        6 2009-07-26 01:50 cdrom -> cdrom0
dr--r--r-- 3 4294967295 4294967295 88 2004-01-01 02:00 cdrom0

```
*snip*


Hello, 

You are comparing two different things here.  The first item listed is designated as a link by the special character 'l' in the first position of the permission block.  We can see from the info at the end of the line that this link is pointed to cdrom0.  

cdrom0 is actually not a normal directory.  The /media/cdrom0 path should be designated in your /etc/fstab file as the mountpoint for /dev/scd0 or something similar.  That means that the cdrom0 'directory' is actually pointed at your cdrom device.  

Unless you have a writable disc in the drive I don't think you would see anything but read permission anyhow.  If not, and you need to enable write/execute permissions, then do so by changing the fstab line that assigns the drive to the mountpoint.  

Does this make sense to you?

---

### Post by Gwendolin on 2009-08-11
Thanks! it does makes sense.

But... my problem apparently is that I don't have permission for cdrom0, and don't know how to change it.
I can't open it as of now!

---

### Post by Gwendolin on 2009-08-11
I solved the problem by following [grahambo2005]("http://ubuntuforums.org/member.php?u=410434")'s solution by droping "udp" attribute for /media/cdrom0 from the fstab file.
see his thread: [B]DVD Rom permission denied

Thanks for the help
[/B]

---

