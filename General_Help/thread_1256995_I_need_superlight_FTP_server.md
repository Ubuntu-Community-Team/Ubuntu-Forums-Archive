---
title: "I need superlight FTP server"
date: 2009-09-03
forum: General Help
---

### Post by Lockheed on 2009-09-03
I need a simple ftp server (one user) to set it up and forget on very low-spec machine (Pentium II, 64mb ram) which also serves for watching movies.

What would be my best (lightest cpu-wise) choice?

---

### Post by theluddite on 2009-09-03
I'm happily using proftpd:  [http://ubuntuforums.org/showthread.php?p=429783](http://ubuntuforums.org/showthread.php?p=429783)

---

### Post by lykwydchykyn on 2009-09-03
> **Lockheed said:**
> I need a simple ftp server (one user) to set it up and forget on very low-spec machine (Pentium II, 64mb ram) which also serves for watching movies.

What would be my best (lightest cpu-wise) choice?

I couldn't say which one was the lightest (ftp servers aren't very resource demanding, even on that hardware), but most can be configured to run with inetd instead of as a daemon, which means they're started on demand and not running the rest of the time.

That's probably the best approach.

---

### Post by P4man on 2009-09-03
You can watch movies on that machine?

---

### Post by Lockheed on 2009-09-03
> **P4man said:**
> You can watch movies on that machine?

Sure can do. LXDE + smplayer = no problems at all. And if you use MoviX, I recon you could even try Pentium 166.

---

