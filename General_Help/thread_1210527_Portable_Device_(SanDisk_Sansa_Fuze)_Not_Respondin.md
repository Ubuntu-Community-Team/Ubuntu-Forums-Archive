---
title: "Portable Device (SanDisk Sansa Fuze) Not Responding"
date: 2009-07-11
forum: General Help
---

### Post by Bradj47 on 2009-07-11
Yesterday I was in a hurry so I unplugged my Sansa without properly ejecting it. When I unlocked my computer today I noticed the Sansa Fuze icon was still there. Here's what I tried in the terminal: 
```

brad@rockstar:/$ cd /media
brad@rockstar:/media$ ls
cdrom  cdrom0  disk-1  floppy  floppy0  LITTLEBUDDY
brad@rockstar:/media$ umount disk-1
/sbin/umount.hal: libhal_ctx_init failed. Is hald running?

```
That's when it was still unplugged. When I plugged it back in there were different errors.
```

brad@rockstar:/dev/disk/by-id$ cd /media
brad@rockstar:/media$ ls
cdrom  cdrom0  disk-1  floppy  floppy0  LITTLEBUDDY
brad@rockstar:/media$ eject disk-1
eject: tried to use `/dev/sdd' as device name but it is no block device
eject: tried to use `./disk-1' as device name but it is no block device
eject: unable to find or open device for: `disk-1'
brad@rockstar:/media$ 

```

Theres another strange thing about this problem. Whether it's plugged in or not, when I open the file browser all the files are there. But when I try to browse using the file browser in Audio Tag Tool nothing shows up. It shows the portable device but when I open it up there's nothing there. Can anyone tell me what's going on or how to fix it?

---

