---
title: "Unable to write &quot;No space left on Device&quot; despite 25% Avail."
date: 2011-12-28
forum: General Help
---

### Post by cyberyaga on 2011-12-28
This issue has me stumped. I have a 2TB hard drive formatted with NTFS. Filled to 76% capacity (459 Gigs free).

I am running into a problem where it doesn't allow me to write anymore to the drive. If I try to create a directory it says: "mkdir: cannot create directory `temp': No space left on device".

If I delete some stuff, it will allow me to write, up until it reaches this point.

Here is the output for df (last line):
```

Filesystem            Size  Used Avail Use% Mounted on
rootfs                131G   12G  113G   9% /
none                  1.5G  304K  1.5G   1% /dev
/dev/disk/by-uuid/46583b02-1ed9-429a-8983-56ccfa48dc91
                      131G   12G  113G   9% /
none                  1.5G     0  1.5G   0% /dev/shm
none                  1.5G  464K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             1.9T  1.4T  459G  76% /media/e

```

I'm running Ubuntu 10.04.2 LTS - XBMCLive Dharma

This behavior does not happen in Windows 7. Also, I've done a complete chkdsk scan on windows 7, and it finds no problems.

Can someone shine a light on what could be causing this problem?

Thanks

---

### Post by collisionystm on 2011-12-28
cd /dev/sdb1

sudo ls -a

look for hidden folders. they will begin with a .

if you have ever deleted anything from ubuntu,  it will store its trash in a folder that starts with .

check the folder to see if its deleted data

Delete the garbage and try again.

---

