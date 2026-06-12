---
title: "How to access windows NTFS drives??"
date: 2010-05-29
forum: General Help
---

### Post by qwerty123321 on 2010-05-29
I used to be able to mount windows hds just fine in any of the linux distros that I've used ..
It always show up in "Computer" and I have an option to mount it but recently I've installed xubuntu and I can't seem to find "Computer" anywhere nor can I find my windows hardrives..
Can someone tell me how I could mount my windows hardrive on xubuntu??
Also..I can't seem to find "Computer" under places :/..whats up with that

---

### Post by Ozymandias_117 on 2010-05-29
I don't know about Xubuntu, but the command line to mount it is:

First, you'll have to use ```
sudo fdisk -l
``` to figure out which partition/drive it is. Find the /dev/sd* for it.

Next, make a directory to mount it in:
```
sudo mkdir /media/windows
```

Now, mount it:
```
sudo mount -t ntfs /dev/sd* /media/windows
```

---

