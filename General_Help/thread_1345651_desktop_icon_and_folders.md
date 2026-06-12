---
title: "desktop icon and folders"
date: 2009-12-04
forum: General Help
---

### Post by miko5054 on 2009-12-04
i deleted few folders from my desktop normal files folder`s music

after i restert the computer   evrthing on the desktop are gone i cant find it in the home folder and it`s look like it deleted how can i recover the files???

i want to recover all the desktop folder....

thnx miko

---

### Post by IllegalCharacter on 2009-12-04
Well you can try following these directions here: [http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html](http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html)

However normally once you delete files, they are difficult to restore and it's unlikely you'll be able to get them back. The more you use the computer too the more likely that you won't get them back.

---

### Post by pietro_spina on 2009-12-04
0: Make sure that if you plan to use it, mount the partition that has the deleted data as **read only**
1: check your trash
2: check Places--> Desktop
3: To see if it is just a Nautilus glitch or if the files are deleted open a termial and cd to the folder and list it's contents

```
cd ~/Desktop && ls
```

4: If the content is gone then check out the DataRecovery wiki
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

5: recovery tools for ext2 ext3 fat32 are pretty well established but you might have to do some serious research if you are using ext4

A while back I remember a very clear headed and detailed forum post helping someone in your situation... but I can't seem to find it. You might want to look around a bit... But keep your wits about you and good luck.

-peter

---

### Post by pietro_spina on 2009-12-04
Hmmm- I'm wondering if you are just missing your "desktop" icons?

In terminal
```
gconf-editor
```
Choose apps->nautilus->desktop

Tick the box beside *computer_icon_visible*, *home_icon_visible*, and *trash_icon_visible*. The changes take effect immediately.

---

