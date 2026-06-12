---
title: "Backup software recommendations"
date: 2012-05-23
forum: General Help
---

### Post by RPGillespie on 2012-05-23
I have an ubuntu box running server edition. It is currently running a file server (samba) and a web server (lamp), and working like a charm. I want to add software that will automatically reach out and backup specific folders on specific computers on the network every once in a while (once a week maybe).

Does anyone have any software recommendations for a home backup solution?

Thanks

RPG

---

### Post by cortman on 2012-05-23
> **RPGillespie said:**
> I have an ubuntu box running server edition. It is currently running a file server (samba) and a web server (lamp), and working like a charm. I want to add software that will automatically reach out and backup specific folders on specific computers on the network every once in a while (once a week maybe).

Does anyone have any software recommendations for a home backup solution?

Thanks

RPG

Write your own rsync or cp script. It's an easy, fun exercise and you can custom tailor it to fit your specific needs.
I use my own scripts but I've heard good things about [Back in Time]("http://backintime.le-web.org/").

---

### Post by markbl on 2012-05-23
I've been using rsnapshot for years to do this. I install deltacopy (windows rsync server) on my wife's windows pc to pull files from there also. Rsnapshot keeps daily, weekly, etc snapshots but uses rsync and links to do this without using much extra disk space. I run it daily out of cron.

---

