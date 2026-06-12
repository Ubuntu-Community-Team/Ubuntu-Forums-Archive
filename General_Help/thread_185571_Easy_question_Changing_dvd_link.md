---
title: "Easy question: Changing dvd link"
date: 2006-05-31
forum: General Help
---

### Post by grsing on 2006-05-31
I have two DVD drives, and for whatever reason, the system defaulted to making the DVD-RW (hdd) the drive linked to the dvd link (so when I play a DVD as a DVD disc in xine, it looks for the DVD in that drive).  I'd like to change that dvd link to point to hdc, which is just a normal DVD drive.  I'm sure it's easy to do it, I'm just not sure what it is (I looked in the wiki, but couldn't find anything).  Thanks!

---

### Post by grsing on 2006-06-01
Bump!  Though I know the boards are running incredibly slow, and everyone is excited about Dapper finally being released (with good reason).

---

### Post by grsing on 2006-06-03
For anybody searching who finds this, it's a pretty simple solution.  Delete the original, and make a new link:

sudo rm /dev/dvd
sudo ln -s /dev/hd? dvd

(replace the ? with the appropriate letter for your drive)

---

