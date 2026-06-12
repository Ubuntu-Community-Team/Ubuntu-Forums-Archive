---
title: "Foremost 1.5.5 segfaults on Ubuntu 9.04"
date: 2010-02-21
forum: General Help
---

### Post by Cubytus on 2010-02-21
Hi all, 

my father had a crash or made a wrong manipulation on its Ubuntu box (he doesn't remember, as most non-techies), and now all the files have vanished from the desktop. He took a look in the garbage, to no avail. 

While I instructed him to avoid using the machine until I tell him of the contrary, I apt-got **foremost 1.5.5** to try to look for lost files on the partition (**/dev/sda3**) with this command line:
**sudo foremost -w -i /dev/sda3 -o /media/disk/fm** (/media/disk is a SATA hard disk larger than the hard drive being recovered, that I plugged in USB since that box doesn't come with SATA ports. It's formatted as ext3, same as the partition being recovered)

However, after a few minutes, it segfaults, then quits. Resources I could find on the Internet are aware of a similar bug, but only for pre 1.5.3 foremost version.

I tried adding the **-s 100** switch to skip the first few sectors, but it didn't work.

I also scanned the ~/Desktop folder with PhotoRec, but it didn't show anything,

My father is growing impatient, and I'm not able to keep on trying on this box all day long.

Am I missing something, both in methodology and execution? What should I be looking for in which one of the log files?

---

