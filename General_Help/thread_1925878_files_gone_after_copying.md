---
title: "files gone after copying"
date: 2012-02-15
forum: General Help
---

### Post by iamhealed on 2012-02-15
hello everyone,

i have just installed ubuntu 11.10 and i'm a newbie. I have an external hard disk and i have files there that i copied to my home folder in my laptop under Documents. The folder was huge since it contains several files. I needed to restart my computer because I was updating it so I canceled the copy operation and rebooted.

Afte that, I was surprised that the files that I have copied from the external hard disk were gone. The folder was there but it was empty. I checked the files in my laptop..the files were copied but of course it was incomplete because i decided to stop the operation.

anyone out there can help me? I am pretty sure that I copied it. I really needed the missing files. I think this happens everytime i copy something from a removable device..and always end up missing those files after copying.

i hope anyone here can help me!
godbless!

---

### Post by aeiah on 2012-02-15
sounds like you're moving rather than copying. how are you doing the copy, by dragging folders from one file mananger window to the other, selecting copy, using the terminal?

are you sure the external drive is mounted (are there other files present on the device)?

---

### Post by iamhealed on 2012-02-15
i right click on the folder from the external hard disk and go to home > documents and paste it there.

i copied it that way.

and yes the drive is mounted..other files are still there but the one that i copied was gone.

---

### Post by iamhealed on 2012-02-15
> **aeiah said:**
> sounds like you're moving rather than copying. how are you doing the copy, by dragging folders from one file mananger window to the other, selecting copy, using the terminal?

are you sure the external drive is mounted (are there other files present on the device)?

supposed it was moved, is there anyway in ubuntu that i can recover the missing files?  the files that were not copied.

---

### Post by sudodus on 2012-02-15
Do you know the name or extension of any of the files? In that case you can search for it with ***find***.
```
sudo find / -name "filename.ext"
```
or 
```
sudo find / -name "filename.*"
```
or
```
sudo find / -name "*.ext"
```
Also check in the trashcan!

If no luck, probably Ubuntu thought the files were written to the next location and then deleted them from the old location. But 'delete' means delete from the table in the file system. The file data are still there and can be recovered by ***photorec***. Browse the internet for photorec and learn about it!

---

### Post by hildenbrandsteven on 2012-02-15
Use the cp command... stop doing everything with a GUI.

Open terminal or whatever CLI client you use..

cd <direct with file>
cp <file> <new directory>

k done

---

