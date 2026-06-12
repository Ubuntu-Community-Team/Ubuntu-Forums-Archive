---
title: "Folder that always has 777 permissions?"
date: 2011-01-03
forum: General Help
---

### Post by undecim on 2011-01-03
I have a folder that I would like to be completely a public directory. THat is, I want every file and subfolder to always have 777 or be treated as if it had 777 permssions.

Only way I can think to do that is with a cron job to check it a couple times an hour. Is there as better way to do this?

---

### Post by ridgeland on 2011-01-04
Change the default mask in /etc/profile
$ sudo gedit etc/profile
default is mask 022 -> all new files are 755
change to mask 000 -> all new files are 777

But that is global not just one folder.

Roll Tide

---

