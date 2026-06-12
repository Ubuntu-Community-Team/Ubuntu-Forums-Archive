---
title: "Keyboard: 'Alt Gr' seemingly maps to 'Alt'"
date: 2010-08-30
forum: General Help
---

### Post by rakydude on 2010-08-30
Dear forum users,

It seems that when I'm pressing the 'Alt Gr' button on my keyboard I get the same result as when pressing 'Alt'. It seems to have happened over night, and I have no idea how to fix it.

My keyboard-layout seems to be correct: Generic 104-key PC, Norwegian,
and I'm running the latest version of Kubuntu.

It's really critical, because it makes a lot of keys on my keyboard unavailable, which in turn makes it impossible to do my programming assignments.. :(

If I don't find a fix to this ASAP I will have to re-install..

Can someone please help me?

---

### Post by rakydude on 2010-08-30
It now works again.

I don't know why, but this is what I did.

1) I renamed ~/.kde/share/config to config.bak
2) I killed the X-server and logged back in
3) KDE had now made me a new folder (~/.kde/share/config) and 'Alt Gr' just worked
4) When I copied back the files, 'Alt Gr' never stopped working, even when I logged out and then back in.  ( Magic!! )

---

