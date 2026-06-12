---
title: "Shell script to mount/unmount vista and open with dolphin"
date: 2009-09-24
forum: General Help
---

### Post by Intrepid Ibex on 2009-09-24
Hi,

I'd really like to have a script on my KDE that when I'd run the script, it would ask me (with a pop-up) if I wanted to **mount** (if it **wasn't** mounted) my Windows partition (it would also open the location with dolphin) and to **unmount** (if it **was** mounted). Is this possible with a script?

Well anyway, if someone with the ability to help me with this but didn't get the point, here is my pathetic attempt to try to explain. I don't think this is even a script :P:

```
if /media/windows; mounted
   then popup "Windows not mounted, mount?": ask; yes | no
      yes; sudo mount /dev/sda2 /media/windows && kdesudo dbus-launch dolphin /media/windows
      no; exit 0
if /media/windows; not mounted
   then popup "Windows already mounted, unmount?": ask; yes | no
      yes; sudo umount /dev/sda2
      no; exit 0
```

---

### Post by Intrepid Ibex on 2009-09-27
Hmm.. well partial solution was: 
```
sudo mount /dev/sda5 /media/windows || sudo umount /media/windows || kdesudo dbus-launch dolphin /media/windows
```

Anyone got improvements?

---

### Post by Intrepid Ibex on 2009-10-01
I'm not a big friend of **bump**ing but no one has a clue ;__;?

---

### Post by Intrepid Ibex on 2009-10-04
bump

---

### Post by mechro on 2009-10-04
My advance apologies for not really answering your scripting question but...

Have you tried KDiskFree? Even on my Gnome desktop it mounts/unmounts drives/partitions and opens in Dolphin.

---

### Post by Intrepid Ibex on 2009-10-05
Cool, anther solution, thanks.

---

