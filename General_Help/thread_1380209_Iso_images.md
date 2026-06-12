---
title: "Iso images"
date: 2010-01-13
forum: General Help
---

### Post by fknyeah on 2010-01-13
Is it possible to run a .iso without putting it onto a disc?

---

### Post by MelDJ on 2010-01-13
i think the command is:
mount -t iso9660 /dir/to/file.iso /mnt/dir/for/iso -o loop

---

### Post by doas777 on 2010-01-13
yes and no, depending on what you mean by "run". the mount loop will work fine if you just need to access files. there doesn't seem to be a way to mount it in a "virtual cd/dvd" drive though, so all it will be is a volume of files.

---

### Post by sarin_cv on 2010-01-13
or u can use gmount-iso from repos...

---

### Post by Forbees on 2010-01-13
> **sarin_cv said:**
> or u can use gmount-iso from repos...

gmount works perfectly on my netbook :)

---

### Post by snowpine on 2010-01-13
You can try Unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ooloo on 2010-01-13
The mount command only mounts the filesystem on a device.

---

### Post by doas777 on 2010-01-13
> **ooloo said:**
> The mount command only mounts the filesystem on a device.
do you know of any way to make it appear to be a disk in the drive?

---

### Post by Judge P on 2010-01-13
Hi

If you want to play an iso file that you have on your computer, I use VLC media player it work very well. You can download it from the Ubuntu software centre.
Regards
JP

---

### Post by Forbees on 2010-01-13
with gmount it will appear like a disk

---

### Post by ooloo on 2010-01-13
> **doas777 said:**
> do you know of any way to make it appear to be a disk in the drive?
You mean like how Windows uses D:, E:, etc? Nope. Linux doesn't mount devices like that usually and they're found in either media/ /mnt or sr0 I think is my disc drive

---

### Post by Forbees on 2010-01-13
you can use sudo comands to make a new folder in the media section to mount the disk to and name that folder D or w/e. but what i thought he was going for was just that the disk will show up in the volumes section of the UBR "desktop"

---

### Post by doas777 on 2010-01-13
> **Forbees said:**
> with gmount it will appear like a disk
but will it appear as an optical disk? eg: you mount the disk, and then tell VLC to play a disk, will it see it? usually the mount loop, and the archive mounter, and whatnot mount it as a hdd, and as a result, any app looking for content on an optical drive specifically, fails.

---

### Post by doas777 on 2010-01-13
> **ooloo said:**
> You mean like how Windows uses D:, E:, etc? Nope. Linux doesn't mount devices like that usually and they're found in either media/ /mnt or sr0 I think is my disc drive
yeah, I know. it just seems like when you tell a media player to play a disk, it ignores any iso mounts, and will only use the physical optical drive. I'm looking for a way to get my system to pretend that it has two optical disk drives (only one physical), and that when i mount an iso, it will appear to the system to be one of those drives. Daemontools does this in windows, but there doesn't seem to be a corollary.

---

