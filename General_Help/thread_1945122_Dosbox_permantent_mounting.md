---
title: "Dosbox permantent mounting"
date: 2012-03-22
forum: General Help
---

### Post by Subidubi32 on 2012-03-22
Hi, I intsalled Dosbox recently, and can you tell me how to mount a drice like c:\ permanently, so when I launch dosbox, I could reach C:\ without typing the mounting section?

---

### Post by papibe on 2012-03-22
Hi Subidubi32.

I believe what you are referring to is the equivalent of going to 'Computer' and double click your Windows partition so that your Windows files became available (usually mounted at /media/disk_name).

To accomplish that automatically, you can add an entry in the file /etc/fstab

That file has a special format so order to write the proper line, we need some details about your disks. Could you post the results of these two commands?
```
sudo fdisk -l

sudo blkid 
```
Regards.

---

### Post by Subidubi32 on 2012-03-22
not exactly, I use dosbox, to play some older games, because it can handle exe, since it is a dos emulator. But before you can reach any file, you have to mount a drive, so mount a folder to be a virtual drive. Sorry, for may bad English. 
Example:terminal
dosbox
mount c: /home/username/dosgames
C:\
cd simfarm
simfarm.exe
                         whatever...
So i would like to skip the first line in dosbox, or the firs two..
Thanks for trying understand me! :)
Subidubi32

---

### Post by Subidubi32 on 2012-03-22
Ok! Found the right answer!

---

### Post by Subidubi32 on 2012-03-22
open gedit /home/'user'/.dosbox/dosbox-0.74.conf
at the end of the file you will find the [autoexec] section
type in the commands, and they will run automaticly when you start dosbox.
for me:

keyb hu
mount c: /home/subidubi/DosGames
C:\

---

### Post by papibe on 2012-03-22
Great!

It would be very nice if you post what you learned so others can take a look at it too.

Regards.

---

### Post by Subidubi32 on 2012-03-22
I posted it! ;) Regards

---

