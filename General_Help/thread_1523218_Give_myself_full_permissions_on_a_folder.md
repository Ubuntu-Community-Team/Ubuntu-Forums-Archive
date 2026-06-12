---
title: "Give myself full permissions on a folder??"
date: 2010-07-03
forum: General Help
---

### Post by Insanexyz on 2010-07-03
Hey,
i need to copy the contents of a dvd to a location on the hdd

```
sudo cp -r /media/UDF\ Volume/ /blah/
```the problem is that i dont have permission to "see" the files on the dvd according to the error. I tried using sudo -i and then attempting to cp but didn't work anyway.. Does anyone know the command that changes user permissions to files? Thanks
Edit:

i tried this too:
```
sudo chmod u=rwx /media/UDF\ Volume/thedirectoryineedpermissionsfor
```Ironically it states "cannot access 'certain directories/files': Permission denied."
There are some very important files on the dvd and i need them really badly, please help.

---

### Post by prodigy_ on 2010-07-03
Well, it's understandable why chmod doesn't work on a **read-only** filesystem which any DVD undoubtedly is. Try ```
sudo ls -l /media
``` to see what's happened with permissions on your mount points.

Also maybe your files are locked by some application accessing them at the moment.

---

### Post by Insanexyz on 2010-07-03
Running that returns:
```
total 4
lrwxrwxrwx 1 root   root      7 2010-06-27 10:05 floppy -> floppy0
drwxr-xr-x 2 root   root   4096 2010-06-27 10:05 floppy0
drwx------ 3 insane insane  100 2010-07-01 14:59 UDF Volume
```
which tells me that i should have rwx permissions on the dvd..?

plus there are no applications running that could possibly be using any data from the DVD

---

### Post by dino99 on 2010-07-03
if your dvd is commercial, drm fight against copy due to rights (legal)

---

### Post by 3Miro on 2010-07-03
I have seen legal DVDs to be have "hidden" files and you will have to mount them in a special way.

You can try:
```
 sudo mount -o remount,unhide /dev/cdrom 
```
Hopefully this will work.

---

### Post by Insanexyz on 2010-07-03
The DVD is not commercial at all, burnt at home and just contains random files which have no reason to be protected. It was burnt on windows though and some permissions probably got changed.

Unfortunately that command returns this: :(
```
sudo mount -o remount,unhide /dev/cdrom/
mount: can't find /dev/cdrom/ in /etc/fstab or /etc/mtab
```

---

### Post by Insanexyz on 2010-07-03
Shameful noob bump.

---

### Post by Insanexyz on 2010-07-03
bamp

---

