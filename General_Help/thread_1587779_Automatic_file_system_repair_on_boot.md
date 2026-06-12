---
title: "Automatic file system repair on boot"
date: 2010-10-04
forum: General Help
---

### Post by megabuffen on 2010-10-04
Hi!

I'm using Ubuntu Lucid and any sudden power loss will usually cause problems with the file system. When I bring the computer back up, Ubuntu will then scan for errors at boot-time and if any errors are found it prompts me to select whether to repair or ignore them. I would much rather have it select the repair option automatically so that I don't have to be physically present.

The reason for this is that i have a web server that should come back online automatically after a power loss.

Any help would be much appreciated.

---

### Post by dcstar on 2010-10-04
> **megabuffen said:**
> Hi!

I'm using Ubuntu Lucid and any sudden power loss will usually cause problems with the file system. When I bring the computer back up, Ubuntu will then scan for errors at boot-time and if any errors are found it prompts me to select whether to repair or ignore them. I would much rather have it select the repair option automatically so that I don't have to be physically present.

The reason for this is that i have a web server that should come back online automatically after a power loss.

Any help would be much appreciated.
```

sudo gedit /etc/default/rcS
```
FSCKFIX=yes

---

### Post by megabuffen on 2010-10-04
Thanks, I'll try it out as soon as my ISP has fixed my internet connection.

---

