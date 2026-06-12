---
title: "Help! file mv in terminal gone awry"
date: 2011-07-06
forum: General Help
---

### Post by Sebastian-Li on 2011-07-06
Plz help!! 

i made a mistake and 'moved' my file to a location called 'sdb'. I forgot to make the target dest.  /dev/sdb

i was trying to be clever and do this from the terminal :( 

the command was: 

mv /sebastian/matthew/Videos/gokarting-02Jul2011.avi sdb

I can't find my file anywhere using 'locate gokarting-02Jul2011.avi' !! 

where would Ubuntu have put it? Can't I undo this? Is there is log of file operations I can check or something? 

it must still exist somewhere. i'm prety sure the available HDD space hasn't changed (it was a big file)

:(

---

### Post by Grenage on 2011-07-06
I would expect the file itself to have been renamed to sdb, in whatever directory you ran the command from.

---

### Post by Sebastian-Li on 2011-07-06
yes you were right! i found it!! thanks so much :D

---

### Post by Grenage on 2011-07-06
That's what we're here for. ;)

---

### Post by kaldor on 2011-07-06
Just to chime in.

The *mv* command is also used to rename files. If you don't include a valid path, the file will be renamed instead of moved.

---

### Post by mcduck on 2011-07-06
> **Grenage said:**
> I would expect the file itself to have been renamed to sdb, in whatever directory you ran the command from.

+1 one to this. The file is now called "sdb" and is located in the directory where you ran the mv command.

Anyway, the whole idea of what you are trying to do is not going to work. You can't move files to hard drives by moving them to the device node, instead you mount the drive and move the file to the mountpoint. (for example you'd mount /dev/sdb1 into /media/sdb1, and then copy the file into /media/sdb1)

Also "dev/sdb" would most likely be wrong, that's the disc itself, while you probably want the first partition of the disc, /dev/sdb1, instead.

---

### Post by Sebastian-Li on 2011-07-09
thanks again for all your comments - i just love it that so much help is avaialble here. i think i'm going to be back more often!

---

