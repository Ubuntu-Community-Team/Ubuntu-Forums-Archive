---
title: "Can't log in from terminal mode"
date: 2011-03-17
forum: General Help
---

### Post by tweezak on 2011-03-17
Ubuntu 10.10

I'm trying to install Nvidia drivers and need to get out of X to do so. I hit Ctrl+Alt+F1 and am asked for my login.

I enter my login and password and get kicked right back to the login prompt after this message:

Cannot execute ksh: no such file or directory

I had switched to ksh by default back when I first installed Ubuntu. I am afraid I don't remember what changes I had to make in order for it to be default for me but there's obviously some script I edited that is running at boot time.

I tried doing this:

```
sudo usermod -s bash username
```but then I just get the same complaint but it says it can't execute bash now.

Does anyone have any ideas where I might have set my configs for shell preference?

Thanks

---

### Post by tweezak on 2011-03-17
I don't know if it matters (ie: whether things may have ended up in different places) but this Ubuntu install started out as a Wubi 10.04 install and was later migrated to a different drive and then upgraded to 10.10.

I think that's the sequence. The upgrade to 10.10 may have happened before I migrated from wubi to a real drive.

---

