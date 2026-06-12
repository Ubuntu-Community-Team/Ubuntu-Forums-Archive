---
title: "metapage_read_end_io: I/O error"
date: 2011-06-11
forum: General Help
---

### Post by jgauthier on 2011-06-11
Greetings all,

  Running mythbuntu based installation, I upgraded to 11.04 a couple weeks ago.  Since doing so, I've been having some troubles.

After a period of idle of time, the machine will go to sleep.  It will then wake itself up when it's time to do some recordings (or someone wakes it up).

Well, i've noticed 30 minutes after it awakes, this messages starts logging to kern.log and syslog:
metapage_read_end_io: I/O error

Not just once.. repeatedly. Until the disk is full :( (about 18G)

I prevented the machine from sleeping, and the problem has gone away.  During this time of sporadic errors message, by attached USB drive acts weird.  So, I'm certain this is a USB drive issue, but I'm also certain it's not a hardware error.  It was introduced with this version (kernel 2.6.38)

If there are any suggestions, I'd appreciate it!

Thanks!

---

### Post by jgauthier on 2012-04-24
Well, so much time has gone by, including many upgrades, including the kernel to 3.x.

This problem still exists!  I would really like to suspend this equipment. I wonder if there is a way to unload the USB stack completely and reload it, and if that would even help.

---

