---
title: "Shared folder between windows host and ubuntu guest"
date: 2011-07-31
forum: General Help
---

### Post by donthaveacow on 2011-07-31
Hey everyone, I'm having a bit of trouble setting up a shared folder between my Windows 7 host and Ubuntu 11.04 guest. I have made the shared folder in virtual box, and then added the following line to the end of fstab:
LinuxShare    /Shared    vboxsf    defaults    0    0

The name of the shared folder I created in Windows and added in virtual box is called 'LinuxShare' and the directory that I wish to access this folder through in Linux is /Shared

What else am I missing?

---

### Post by Morbius1 on 2011-07-31
There's no longer any need for a manual mount or an fstab entry for the host share if you are using VBox 4. It's already automatically mounted for you at:
```
/media/sf_share-name
```The "sf_" before the share-name lets you know it's a VBox shared folder.

---

### Post by donthaveacow on 2011-07-31
OMG. That's so annoying... well actually it's good because it's so basic, just annoying that I wasted so much time in fstab :(

Thank you!! :D

---

