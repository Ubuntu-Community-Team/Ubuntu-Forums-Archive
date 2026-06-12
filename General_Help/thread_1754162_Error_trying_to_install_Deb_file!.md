---
title: "Error trying to install Deb file!"
date: 2011-05-09
forum: General Help
---

### Post by TheNerdAL on 2011-05-09
So I'm trying to install VBA-M and I use the deb installer but it gives me an error: 
```
Selecting previously deselected package vbam-sdl.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 183820 files and directories currently installed.)
Unpacking vbam-sdl (from .../vbam-sdl_1.8.0.1001-1_i386.deb) ...
dpkg: error processing /home/adrian/Downloads/vbam-sdl_1.8.0.1001-1_i386.deb (--install):
 trying to overwrite '/etc/vbam.cfg', which is also in package visualboyadvance-m 1.8.0.877-1
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Errors were encountered while processing:
 /home/adrian/Downloads/vbam-sdl_1.8.0.1001-1_i386.deb
```

How can I fix this?
Thanks!

---

### Post by neu5eeCh on 2011-05-09
I had a similar error when trying to install newer software after having tried trial software. The trial software didn't properly uninstall. Did you already have a version of VBA installed?

---

### Post by TheNerdAL on 2011-05-09
> **VTPoet said:**
> I had a similar error when trying to install a newer software after having tried trial software. The trial software didn't properly uninstall. Did you already have a version of VBA installed?

Yeah, the regular VBA.

---

### Post by neu5eeCh on 2011-05-09
That's your problem then. I had the same error installing Textmaker 2010 after using Textmaker 2008.

What I had to do, and what you probably will have to do, is to manually search for 'any and all' remnants of the earlier version. Either remove them (or rename them). I've never used VBA-M, so I can't help you too much. 

Renaming /etc/vbam.cfg won't be enough, probably. Check in your home folder for any hidden files associated with vbam, check /usr/~ and /etc/~ /. Something in the earlier installation is pointing to the vbam.cfg file (I assume).

---

### Post by TheNerdAL on 2011-05-09
> **VTPoet said:**
> That's your problem then. I had the same error installing Textmaker 2010 after using Textmaker 2008.

What I had to do, and what you probably will have to do, is to manually search for 'any and all' remnants of the earlier version. Either remove them (or rename them). I've never used VBA-M, so I can't help you too much. 

Renaming /etc/vbam.cfg won't be enough, probably. Check in your home folder for any hidden files associated with vbam, check /usr/~ and /etc/~ /. Something in the earlier installation is pointing to the vbam.cfg file (I assume).

For some reason, I Can't remove them. D:

Edit: nevermind, I got it.

EDIT #2: Gives me the same error.

EDIT #3: Fixed it, just had to remove any visualboyadvance or VBA things from Synaptic as well.

---

### Post by neu5eeCh on 2011-05-09
Great! Glad to be of help.

---

