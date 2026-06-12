---
title: "Grysnc deleted files"
date: 2011-12-02
forum: General Help
---

### Post by UncleMonty on 2011-12-02
Is there anyway of changing grsync so that it removes deleted files from the back up folders?

---

### Post by aeiah on 2011-12-02
well it uses rsync as the back end, and in rsync you'd use the --delete flag. does grsync allow for you to specify custom flags?

or are you wanting to retroactively delete from previous backup folders?

---

### Post by UncleMonty on 2011-12-02
> **aeiah said:**
> well it uses rsync as the back end, and in rsync you'd use the --delete flag. does grsync allow for you to specify custom flags?

or are you wanting to retroactively delete from previous backup folders?

There is 'execute this command before rsync' do I need to enter --delete in there?

---

### Post by collisionystm on 2011-12-02
> **UncleMonty said:**
> There is 'execute this command before rsync' do I need to enter --delete in there?


grsync should write to the crontab i think

if you open a terminl

crontab -e

do you see an entry for rsync?

you can add the --delete in there

---

### Post by Jacobonbuntu on 2011-12-02
> **collisionystm said:**
> grsync should write to the crontab i think

if you open a terminl

crontab -e

do you see an entry for rsync?

you can add the --delete in there


nono! grsync has nothing to do with cron, it is just a GUI to create rsync backup commands (and execute them). The output of grsync can be edited, which I did not do, but should be easy if you know the syntax. 
You can however also use the outcome of grsync to create automatic backups with cron.

---

### Post by Jacobonbuntu on 2011-12-02
...aeiah's suggestion is right; just open the advanced options tab in grsync and add "--delete" in the additional options section.
files deleted on the source will thus be deleted on the backup location

---

