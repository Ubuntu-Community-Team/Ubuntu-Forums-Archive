---
title: "Meaning of Error during last update"
date: 2006-06-18
forum: General Help
---

### Post by dalee on 2006-06-18
Hi,

I got this error when I ran an update to Dapper yesterday

Installing new version of config file /etc/gnome/defaults.list ...

** (process:9248): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:9248): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed


I can't seem to google any info on it. But everything seems to be working correctly, (even reboots without fail). But I'm concerned that it might cause me trouble at a later date.

Any ideas?

Thanks!
dalee

---

### Post by suziequzie on 2006-06-21
I had the same error messages while trying to add gnome to my Kubuntu machine.  Gnome won't  work properly now, and keeps freezing/crashing, and no windows open properly.  (I did a "sudo apt-get install ubuntu-desktop"... worked fine in 5.10, but not so well in dapper)

So, yeah, if anyone here knows what that means, or how to fix it, please let us know.

---

### Post by suziequzie on 2006-07-03
Got it!!!!

Well, this worked for me.
Edit the file (as root) and replace

Type=Application 

with 

MimeType=application/x-desktop

I've got hundreds (printer gave me 4+ pages of files) to manually fix.

Hope it helps.

---

