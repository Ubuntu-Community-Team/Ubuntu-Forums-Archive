---
title: "XMMS-FLAC Problem"
date: 2006-03-19
forum: General Help
---

### Post by OlineSixtyOne on 2006-03-19
I need to play my FLAC's in XMMS and I like to use replay gain. I installed xmms-flac from the repos and it worked fine except for replay gain.
I went into the preferences, then the FLAC decoder configuration and enabled replay gain. I hit OK then poof XMMS was gone. I started it back up and went to check if replay gain was turned on, and it was not. 

I discovered that if you press OK from within the FLAC decoder settings, XMMS crashes and your changes are not implemented. This makes it impossible to modify the decoder settings to enable replay gain.

I ran XMMS from a terminal to see what the error was. Here it is:
```
andrew@ubuntu:~$ xmms
Message: device: default
*** glibc detected *** free(): invalid pointer: 0xb6d4655e ***
Aborted
andrew@ubuntu:~$
```

---

### Post by OlineSixtyOne on 2006-03-20
Bump.

---

### Post by OlineSixtyOne on 2006-03-20
Bump

---

### Post by OlineSixtyOne on 2006-03-21
Bump

---

### Post by OlineSixtyOne on 2006-03-22
Bump

---

### Post by OlineSixtyOne on 2006-03-22
Yay, bump #5.

---

### Post by OlineSixtyOne on 2006-03-23
Bump.

---

### Post by OlineSixtyOne on 2006-03-23
Bump.

---

### Post by OlineSixtyOne on 2006-03-24
Bump.

---

