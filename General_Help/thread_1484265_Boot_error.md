---
title: "Boot error"
date: 2010-05-15
forum: General Help
---

### Post by SteveO87 on 2010-05-15
Hi all,
i have a login problem with ubuntu lucid.
When i put my password, appear 4 system error that says 
"Failed to open usr/share/pixmaps/lock.png"

I try to boot in recovery mode, but the problem remain. Can anyone help me? 
Thanks!

---

### Post by SteveO87 on 2010-05-15
up

---

### Post by angry_johnnie on 2010-05-15
now, this is just a wild guess, but you could try it.

boot from live cd
mount current linux root partition
copy something (a png image) into /usr/share/pixmaps and rename it to lock.png
make sure it is readable to everyone by executing 
sudo chmod a+rw /your/drive/usr/share/pixmaps/lock.png
re boot

might be worth a try :)

---

