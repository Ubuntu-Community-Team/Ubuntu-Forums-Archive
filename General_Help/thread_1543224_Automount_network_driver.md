---
title: "Automount network driver"
date: 2010-07-31
forum: General Help
---

### Post by doomstone on 2010-07-31
Hello i am trying to get my slave media center to mount a network drive at startup automatic.
I have written this to my /etc/fstab/
```
\\192.168.1.2\root /media/data cifs username=doomstone,password=XXXX,auto,user 0 0
\\192.168.1.2\xbmc /media/xbmc cifs username=doomstone,password=XXXX,auto,user 0 0
```

Now when i do a "mount /media/data" it all works just fine, but it dose not mount it on statup. witch is a pain as the computer dose not have a keyboard, only a remote. So i need to ssh the computer and mount the drives each time i boot.
As far as i can figure is that the computer dose not have a network connection at the mount time, and thus fails the mount of the network drives.

How can i do this so it can be mounted at startup?

---

### Post by doomstone on 2010-08-01
Are no buddy able to help me with this problem? there must be some people who have tryed this before.

---

