---
title: "iocharset=utf8 -- why use that in a vfat / fat32 mount?"
date: 2009-08-08
forum: General Help
---

### Post by swerdna on 2009-08-08
Hi

I've been puzzled by the vfat mount advice that I see around these forums. Frequently the advice is to use this option: "iocharset=utf8".

I see from "man mount" that this option is available in the special options for mounting fat filesystems.

The man page reference is this:
```
iocharset=value
       Character set to use for converting between 8 bit characters and
       16 bit Unicode characters. The default is iso8859-1.  Long file-
       names are stored on disk in Unicode format.
```

So does "iocharset=utf8" say that long file names will be stored as utf8 unicode characters? And can someone elaborate on why this is necessary?

Thanks
Signed
Just Curious

---

### Post by merlinus on 2009-08-08
This example should work fine for fat filesystems:

/dev/sda1 /media/sda1 vfat uid=1000,umask=022 0 0

The uid gives ownership to you, and umask=022 gives read and write permissions only to you.

---

### Post by swerdna on 2009-08-08
I kinda hoped that, and was looking for a confirmation, thanks. It just looked and read like something esoteric, generally unnecessary.

---

### Post by swerdna on 2009-08-08
I've been looking at your suggested mount -- and a few questions if you don't mind (new at this Ubuntu stuff):
[LIST=1]
[*]Is umask=022 unnecessary because it's the default
[*]Is uid=billy better because uid=1000 could be for george or sally
[*]and finally, is uid=billy,gid=billy best because that makes the folder /media/sda1 just like a standard folder in billy's home; i.e. like this: billy:billy drwxr-xr-x
[/LIST] 

I had a bit of trouble with this:> 
The uid gives ownership to you, and umask=022 gives read and write permissions only to youbecause others could read my attached usb drive.

Thanks

PS further edit:
I've now found that this is a pretty good string to mount a "private" vfat partition:```
/dev/sda1 /media/sda1 vfat uid=billy,gid=billy,umask=027 0 0
```that makes the partition to be billy:billy and drwxr-x---, which is more like your suggestion:> umask=022 gives read and write permissions only to you

Is that making sense or am I off the track somewhere?

---

