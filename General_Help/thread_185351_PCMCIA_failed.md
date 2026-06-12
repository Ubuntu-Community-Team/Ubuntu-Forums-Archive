---
title: "PCMCIA failed"
date: 2006-05-31
forum: General Help
---

### Post by Hoffmann on 2006-05-31
Hello:

When I boot Ubuntu Dapper, I get:

Starting PCMCIA services ....Failed.

How can I solve this?
Thanks!

---

### Post by bluevoodoo1 on 2006-05-31
Are you on a laptop [or desktop] that has a PCMCIA slot that you use?

If no, then it's really no problem. 

If it bothers you... you may want to look into this thread...
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Hoffmann on 2006-05-31
[QUOTE=bluevoodoo1]Are you on a laptop [or desktop] that has a PCMCIA slot that you use?

If no, then it's really no problem. 

If it bothers you... you may want to look into this thread...
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)[/QUOTE]

Hello bluevoodoo1,

Since I am not using a PCMCIA slot, I turned it off (by following the informations from the link you sent me).
Many thanks!:D

---

### Post by Ubuntist on 2006-06-06
[QUOTE=bluevoodoo1]Are you on a laptop [or desktop] that has a PCMCIA slot that you use?[/QUOTE]

I get the same error, but most things seem to run OK (a few bugs, but I've no reason to suppose they're related to PCMCIA).

To ask a really stupid question, um, how would I know whether I'm using a PCMCIA slot, or whether I even have one?

---

### Post by James Keating on 2006-06-10
This sounds like what happened to me. It seems common, and appears to be due to a kernel bug.

I tried many approaches, but the one that worked for me came from another Ubuntu thread, by Daniel Carrera. The kernel disables the PCMCIA port during boot because nothing is using it then. You have to insert the modules by hand, then start cardmgr to watch the card.

sudo modprobe pcmcia && modprobe pcmcia_core
sudo cardmgr

Some people say you need to eject and insert the card after activating the modules, but I didn't need to.

---

