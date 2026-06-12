---
title: "boot problem"
date: 2009-12-24
forum: General Help
---

### Post by imousavi on 2009-12-24
when I go 2 the boot menu i c these links
_[IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5409[/IMG]_
when I click on the first link this erorr comes
[IMG]http://ubuntuforums.org/picture.php?albumid=1573&pictureid=5407[/IMG]
what should i do?

---

### Post by imousavi on 2009-12-24
help
:(

---

### Post by adam814 on 2009-12-24
Can you boot with the LiveCD and post your grub.cfg?  Also what filesystem are you using for "/"?

---

### Post by imousavi on 2009-12-25
no i cant reach the os

---

### Post by Leppie on 2009-12-25
you cannot even boot from a livecd?

---

### Post by imousavi on 2009-12-25
i can but that doesn't help because im using with windows (i installed with wubi )
no use of using live

---

### Post by adam814 on 2009-12-25
Wubi installs will fail to boot if the filesystem isn't clean (can't mount any of the filesystems which seems to be the error you're getting).  Maybe Windows didn't shutdown cleanly?  If so you need to login to Windows and run chkdsk /r in a command prompt.

---

