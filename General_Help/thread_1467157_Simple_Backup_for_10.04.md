---
title: "Simple Backup for 10.04?"
date: 2010-04-30
forum: General Help
---

### Post by lakelovers on 2010-04-30
I just did a fresh install of 10.04, and I can't find simple backup (sbackup) to restore my 9.04 files? I backed up all my 9.04 files onto an external drive using simple backup. Where do I fine simple backup for 10.04? Or can I use a different backup app without going through hoops to restore my files?

---

### Post by StuartN on 2010-04-30
> **lakelovers said:**
> Where do I fine simple backup for 10.04?

Simplebackup is in the repositories, if you open Synaptic then it should be listed. (Or sudo apt-get install simplebackup).

---

### Post by 98cwitr on 2010-04-30
^^^not the right command.

> **lakelovers said:**
> I just did a fresh install of 10.04, and I can't find simple backup (sbackup) to restore my 9.04 files? I backed up all my 9.04 files onto an external drive using simple backup. Where do I fine simple backup for 10.04? Or can I use a different backup app without going through hoops to restore my files?

you're gonna have to reinstall it.

*sudo apt-get install sbackup*

---

### Post by lakelovers on 2010-04-30
I tried installing via the terminal using "sudo apt-get install sbackup" This is what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sbackup

I can not find it in Synaptic, either. The search for sbackup in Synaptic brings up "backuppc." I also did a search in the software center. No sbackup. I looked at software sources which seems to show all resources checked.

I found sbackup on the Source Forge site, and downloaded it. It seems into install successfully, However, when I tried to configure it in Synaptic I get this:

**Could not launch 'Simple Backup Config** "failed to execute child process su-to-root (no such file or directory).

I'm stumped.

---

### Post by lakelovers on 2010-05-01
I was trying to access apps before the app sources were updated. Once updated, Sbackup was right where it sould be in Synaptic. Thanks for all your responses.

---

