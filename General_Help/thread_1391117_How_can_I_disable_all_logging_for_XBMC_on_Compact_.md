---
title: "How can I disable all logging for XBMC on Compact Flash install?"
date: 2010-01-26
forum: General Help
---

### Post by dlhoppe on 2010-01-26
Hi,
 
I'm trying to find a way to disable all logging on a compact flash install. I would also like to keep the ability to easily turn it back on when needed. Can anyone advise me on how to disable syslogd and klogd?
 
 
Thanks!

---

### Post by cariboo on 2010-01-26
You can disable logging in advancedsettings.xml, I'm not close to the system I run XBMC on, so I can't tell you it's exact location, 

Have a look at [this ]("http://xbmc.org/wiki/?title=Advancedsettings.xml#.3Cloglevel.3E")page for an explanation.

---

### Post by dlhoppe on 2010-01-26
Thanks. I figured out the xbmc logging. 
 
I need to disable syslogd and klogd. 
 
Anyone?

---

### Post by dlhoppe on 2010-01-26
Ok, I was able to suppress everything but xorg.0.log, dkms_autoinstaller.log and lastlog. If anyone has any suggestions as to how to temporarily turn those off, I'm all ears.

---

### Post by naasking on 2011-04-04
Why not just make /var/log an in-memory file system, ie. tmpfs? Then it won't touch the CF card at all. You'll lose all your logs on each shutdown though. Just have to modify /etc/fstab I think.

---

