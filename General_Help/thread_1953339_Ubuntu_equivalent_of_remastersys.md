---
title: "Ubuntu equivalent of remastersys?"
date: 2012-04-06
forum: General Help
---

### Post by carmenin87 on 2012-04-06
I know PC Linux OS has a built in app that allows users to make a full backup of their computer.

Does Ubuntu something similar that is easy to use so that I can move away from Remastersys.

I am using Ubuntu 10.04 LTS.

---

### Post by Paddy Landau on 2012-04-06
I am not quite sure what you are after. Remastersys is more for making an installation disk rather than a backup.

If you want to back up your data, you can try on-line solutions such as Dropbox, SpiderOak and Ubuntu One; or local solutions such as rdiff-backup and rsync.

If you want to make a disk backup, so that you can restore the entire disk (or just selected partitions if you prefer), look at [CloneZilla]("http://www.clonezilla.org/") and [RedoBackup]("http://redobackup.org/"). (RedoBackup is easier but has some limitations.)

---

### Post by carmenin87 on 2012-04-06
It is actually a disk backup that I would like to make, essentially making a LiveCD of my Ubuntu build.

I know remastersys allows me to do this, I'm just wondering if there is a built in Ubuntu utility that offers the same functionality so that I don't have to go to a third party app.

---

### Post by Paddy Landau on 2012-04-06
No, I have never come across an Ubuntu utility to do this. Incidentally, very few applications are Ubuntu (Canonical) utilities; virtually every one is a third-party app.

If this has answered your question, please mark the thread as solved.

---

### Post by mike555 on 2012-04-06
You might want to read about "relinux" here;
[http://www.howtoforge.com/creating-your-own-distributable-ubuntu-dvd-relinux](http://www.howtoforge.com/creating-your-own-distributable-ubuntu-dvd-relinux)

---

