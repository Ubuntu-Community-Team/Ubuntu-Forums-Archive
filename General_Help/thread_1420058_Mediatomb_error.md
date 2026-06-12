---
title: "Mediatomb error"
date: 2010-03-02
forum: General Help
---

### Post by Sirsteveo on 2010-03-02
> Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2010-03-02 16:37:36    INFO: Loading configuration from: /home/steven/.mediatomb/config.xml
2010-03-02 16:37:36    INFO: Checking configuration...
2010-03-02 16:37:36    INFO: Setting filesystem import charset to UTF-8
2010-03-02 16:37:36    INFO: Setting metadata import charset to UTF-8
2010-03-02 16:37:36    INFO: Setting playlist charset to UTF-8
2010-03-02 16:37:36    INFO: Configuration check succeeded.
2010-03-02 16:37:36    INFO: Initialized port: 49152
2010-03-02 16:37:36    INFO: Server bound to: 192.168.1.101
2010-03-02 16:37:37   ERROR: SQLITE3: (5) database is locked
Query:UPDATE "mt_autoscan" SET "touched"=0 WHERE "persistent"=1 AND "scan_mode"='timed'
error: database is locked


Error: database is locked? why and how to unlock it?

---

### Post by Aerospaztic on 2010-03-12
Do this:

sudo killall mediatomb

And then do this:

sudo mediatomb start

That should fix it.

---

### Post by tgalati4 on 2010-03-12
If you have two instances of mediatomb running they would both be trying to access the same database--hence the lockout situation.

---

### Post by moore.bryan on 2010-03-17
I hate to hijack the thread a bit, but I'm hoping one of you can answer my question. I'm trying to get MediaTomb running on my iMac G4 (PPC), but my Web UI is only blank... no icons, no choices, no nothing. Aren't I supposed to add media?

---

### Post by telm0telm0 on 2010-04-14
My Meditomb is up and running great, and I already added 

<map from="avi" to="video/x-divx"/> 
<map from="divx" to="video/x-divx"/>
for avi support..but it still show unsupported data when I try to stream on my ps3, what am I missing?

---

