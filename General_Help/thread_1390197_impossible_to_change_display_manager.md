---
title: "impossible to change display manager"
date: 2010-01-25
forum: General Help
---

### Post by liberalist on 2010-01-25
Hi everyone,

I looked everywhere on the internet to change my display manager from kdm to gdm, but it always fails. It says that gdm is the default, but I still get the kdm/kde pointer, which I can tell apart from the gdm/gnome one. 

There is a bug on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/414140"), but it is deemed invalid. 

How can I change the login manager manually? So not with sudo dpkg-reconfigure kdm? Also, can I safely remove kdm while it still seems to be in use? Thanks in advance.

---

### Post by warfacegod on 2010-01-25
There should be no issues with removing it as lomg as there is something in place to take over for it.

---

### Post by liberalist on 2010-01-25
So I should just remove it? Setting gdm as default seems "cleaner" though.

---

### Post by warfacegod on 2010-01-25
If it's just the pointer that's bugging you then replace it in Appearance> Themes> Customize> Pointer tab. Otherwise, if you don't want KDE any more then remove it.

---

