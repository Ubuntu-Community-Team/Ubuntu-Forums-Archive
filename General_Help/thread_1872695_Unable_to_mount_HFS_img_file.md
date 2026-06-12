---
title: "Unable to mount HFS img file"
date: 2011-10-31
forum: General Help
---

### Post by Rodayo on 2011-10-31
So I have this .dmg file that I downloaded. I converted it to an .img using dmg2img. 

I tried to mount it using:

```
sudo mount -t hfsplus -o loop myfile.img /mnt
```but I get this error:
> mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soI also tried "-t hfs" and got the same error. If it makes a difference I ran "modprobe hfsplus" as well, beforehand.

This is actually part of a tutorial I'm following on how to convert a .dmg file to a .iso. So if anyone could help do that without bothering with all of this that would be even better =P

---

