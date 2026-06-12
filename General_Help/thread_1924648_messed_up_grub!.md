---
title: "messed up grub!"
date: 2012-02-13
forum: General Help
---

### Post by qwertyjjj on 2012-02-13
Ok, so I upgraded to Natty and lost full speed because cpufreq wouldn;t work.
I then booted from a Live CD and copied everything from my backup.tar.gz back to the hard drive.
However, on booting, I get:
error: invalid extent
error: synch not found grub_os_area_addr

So, I tried the boot repair CD - that didn't fix it.

I then took a CD to upgrade completely and now I have Ocelot but with none of my data.

How can I either:
(a) get everything from backup.tar.gz onto Ocelot (including /home, /var/www, mysql databases) . I don;t mind reinstalling software if I have to.
OR
(b) install from the backup file and get grub working properly?

---

### Post by varunendra on 2012-02-14
How did you create the backup file? If it was properly done using some  partition backup tool or command, then you could use the same  tool/command to restore it. Then fixing  grub (if required) should be easier.

Alternatively, I was wondering if you could install the same version again, then just overwrite the newly installed files/folders with the backed up ones from a live session. But I don't know if that could be done somehow without messing up the 'ownership' and permissions on them.

---

