---
title: "HDD file permissions while using LiveCD..."
date: 2011-09-04
forum: General Help
---

### Post by j*tech on 2011-09-04
I boot the LiveCD (*from the book Ubuntu Unleashed, v10.10*), go to "try Ubuntu", mount my hard drive, go to Terminal and 'gksudo nautilus'...I access my filesystem, but I can't copy/ paste any of the files from it (want to put them on USB)...Can I somehow "login" to my admin profile to access my /home files?  Or can I use terminal and change the file permissions of the whole drive, and how would I do that :???: lol?

---

### Post by j*tech on 2011-09-05
Anyone?

---

### Post by Johnb0y on 2011-09-05
what was the previous file system format and which OS? :)

---

### Post by j*tech on 2011-09-05
Ubuntu 11.04, i believe ext2

---

### Post by Johnb0y on 2011-09-05
have a look at the foolowing: it should help you...

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

could also try:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by j*tech on 2011-09-05
Solved...I thought it was a file permission problem but it was my flash drive #-o (not to long ago formatted in XP)...I guess Ubuntu couldn't recognize it, so I reformatted under LiveCD, and voila!

---

