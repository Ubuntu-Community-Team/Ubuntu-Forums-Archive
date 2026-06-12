---
title: "Having boot up problems"
date: 2009-11-07
forum: General Help
---

### Post by MetroidJunkie2008 on 2009-11-07
It crashed in the middle of updating drivers and now it can't boot up. It gives the following:


```

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
ESC for recovery shell
/: Waiting for dev/desk/by-uuid/8b0b237-ed07-4d04-bc76-dcabd47d5aa5
/tag: waiting for (null)
tmp: waiting for UUID=06232910-a1f9-4712-b18b-1ba4e918ffc9

```

Trying to boot into recovery mode seems to just make it hang at some generic process. I'm able to access the HDD with the demo version on the cd, any suggestions?

Note: This is Ubuntu 9.04, both the version I currently have and what's on the disc.

---

### Post by MetroidJunkie2008 on 2009-11-07
Can nobody offer a suggestion?

---

### Post by drs305 on 2009-11-07
Use the recovery mode to boot to a root prompt.
Open /etc/fstab with nano: (nano /etc/fstab)
Place a comment in front of the line with uuid 8b0b237-ed07-4d04-bc76-dcabd47d5aa5 (hopefully not a system partition).
Save the file (XTRL-X, Y, Enter)
Reboot.

---

### Post by MetroidJunkie2008 on 2009-11-07
Error writing, read-only file system.

---

### Post by MetroidJunkie2008 on 2009-11-07
Okay, I managed to do it manually through the demo version by giving myself permission through chown but I don't know what you meant by "a comment" so I placed a # infront of it, it didn't do anything. Still gives the same error booting up.

---

