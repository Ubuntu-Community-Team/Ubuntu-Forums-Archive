---
title: "Can't set keyboard layout options."
date: 2010-05-14
forum: General Help
---

### Post by Brodie337 on 2010-05-14
Hi all, I've got an odd problem with the keyboard layout options.

I use caps as an additional control, as set in Keyboard Preferences > Layout > Options. However, I recently came across an issue where Shift + Space does not send space, so I go into the options to set space at any level to fix it, and while the option appears to have been selected, there is no change in behavior.

Whats going on?

EDIT: If I open it, and set caps back to caps, it works. However, if I reopen it, and change the spacebar, caps reverts to control.

---

### Post by Brodie337 on 2010-05-14
Any ideas?

---

### Post by Brodie337 on 2010-05-15
OK... Plan B.

Is there some way to manually set these options in 10.04, by editing a conf file?

---

### Post by Brodie337 on 2010-05-15
OK... found half of the problem.

Because Ialso use an xfce environment, I had /usr/bin/setxkbmap -option "ctrl:nocaps" running at startup to change to my layout, however, I still have a problem with Shift +Space not sending space, no matter what it is set to under layout options.

Any help out there?

---

