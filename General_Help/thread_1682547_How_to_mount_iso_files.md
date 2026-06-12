---
title: "How to mount iso files"
date: 2011-02-06
forum: General Help
---

### Post by jimmys_ on 2011-02-06
Is there any tool that mounts iso files and lets you view them as virtual drives?
I already tried Gmount-iso, AcetoneISO, Furius ISO Mount and the custom command mount to mount my iso in a directory. All three tools failed to mount my iso and I don't understand why. Mounting using the command succeeded but inside the iso I have some files that I want to execute but are not marked as executables and therefore I cannot execute them.
Does anyone knows what to do?

---

### Post by dino99 on 2011-02-06
iso is basicaly an archive, so extract the files inside then chmod

---

### Post by gufide on 2011-02-06
open with archive mounter

---

### Post by hawthornso23 on 2011-02-06
The simple commandline method.

Make sure the directory /media/iso exists (create it if needed). Then change to the directory with your.iso in it and run 

```

sudo mount -o loop -t iso9660 your.iso /media/iso

```Mounting to a subdirectory of /media means that the iso will then appear as a disk on your desktop exactly as if you had inserted a CD or DVD.When you are finished, unmount using 

```

sudo umount /media/iso

```Note that this method will fail if the iso is made from a copy protected disk.

---

