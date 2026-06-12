---
title: "automatic backing up"
date: 2006-06-22
forum: General Help
---

### Post by styven on 2006-06-22
Hi all,

I would like my home folder to automatically back itself up to an external hard disk.

I am looking to set this up so that if i update/delete a file, change folders, these actions are duplicted on the external drive on going.

There seems to be something called rsync, but not sure if this is what i require.

regards Steve

---

### Post by jimbren on 2006-06-22
I use rsync to do my backups to an external disk and it works great.  I set it as a cron job and forget about it.

Here's a very good site that will tell you just about everything you need to know, complete with examples to enter into your crontab or the command line.
[http://rsync.samba.org]("http://rsync.samba.org/")/

---

### Post by styven on 2006-06-22
Thank for that,

I take it that this is a command line tool only.

What is a cron job, cron tab?

I see the example that shows "backup to a spare disk", does this do it on the fly or at a certain time or daily?

Sorry for more questions, but this looks daunting at the moment!

Steve

---

### Post by ifokkema on 2006-06-23
Also, you could try and take a look at unison. Perfect and fast to mirror two directories.

---

