---
title: "$HOME/.dmrc permissions problem"
date: 2009-09-04
forum: General Help
---

### Post by Big Gaz on 2009-09-04
Hi all,

I have a pop up window appear shortly after i enter my user name and password.

it says: -

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others.

When I look at the permissions it get RW for me and R for all others.

I have also carried out a chmod 644 /.dmrc just to make sure.

Where am i going wrong?

---

### Post by bacardiandwatermelon on 2009-09-04
[http://ubuntuforums.org/showthread.php?t=1227652&highlight=dmrc](http://ubuntuforums.org/showthread.php?t=1227652&highlight=dmrc)

---

### Post by unutbu on 2009-09-04
This guide should help:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by Big Gaz on 2009-09-04
Thanks Guy's, worked a treat

---

