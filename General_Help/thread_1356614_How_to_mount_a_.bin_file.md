---
title: "How to mount a .bin file ?"
date: 2009-12-16
forum: General Help
---

### Post by Physical Hook on 2009-12-16
```
sudo mount ./i-vtcalp.bin mnt
[COLOR=Red]mount: /home/dainis/VTC/i-vtcalp.bin is not a block device (maybe try `-o loop'?)[/COLOR]

```

```
i-vtcalp.bin: data
```

Any ideas ?

---

### Post by DaVince21 on 2009-12-16
```
sudo mount -o loop ./i-vtcalp.bin mnt
```
Assuming 'mnt' is the mountpoint in your current directory, of course.

You could also install fuseiso and mount the drive with:
```
fuseiso imgfile ~/mountpoint
```
Where ~/mountpoint can be any directory in your home directory, really (~ means /home/username). Upside on this is that you don't need root privileges to mount the file, and you can mount a few more different filetypes than with the normal mount command.

---

### Post by Physical Hook on 2009-12-16
```
[COLOR=Red]mount: you must specify the filesystem type[/COLOR]

```

---

### Post by DaVince21 on 2009-12-16
That means that mount doesn't know how to handle the file type. Install and try fuseiso. Unless you're sure that the filesystem type is ISO9660 (standard CD-ROM/DVD-ROM image), then you can add -t iso9660 to the command. But those usually have the .iso extension, not .bin.

---

### Post by Physical Hook on 2009-12-16
fuseiso did the trick. Thank you :)

---

### Post by EricDrijv on 2009-12-16
If the bin file is a svcd Gnome-mediaplayer can play it without mounting:guitar:

---

### Post by Physical Hook on 2009-12-16
> **EricDrijv said:**
> If the bin file is a svcd Gnome-mediaplayer can play it without mounting:guitar:
It's not an SVCD file.

---

