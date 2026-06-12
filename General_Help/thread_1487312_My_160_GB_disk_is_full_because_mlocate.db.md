---
title: "My 160 GB disk is full because mlocate.db"
date: 2010-05-18
forum: General Help
---

### Post by lmicu on 2010-05-18
I have this:

root@lucian-laptop:/var/lib/mlocate# ls -lh
total 122G
-rw-r----- 1 root mlocate 7.3M 2010-05-08 08:03 mlocate.db
-rw------- 1 root root     61G 2010-05-18 20:09 mlocate.db.4xfaBr
-rw------- 1 root root     40G 2010-03-28 03:18 mlocate.db.eAIFn8
-rw------- 1 root root     11G 2010-04-25 15:23 mlocate.db.ppE9Il
-rw------- 1 root root    273M 2010-02-28 11:48 mlocate.db.rTzhmB
-rw------- 1 root root     11G 2010-03-14 15:42 mlocate.db.ub4Evy


I am not sure who is creating this.

Let me know if you have any ideas.

---

### Post by madverb on 2010-05-18
That's very strange. mlocate is just a database of all the files in your root directory which is for searching purposes.
When you use the command 'locate' to find files it uses this database.
You should be fine to delete all the files but leave mlocate.db.
I'm not sure why it is creating all those huge files.

---

### Post by tgalati4 on 2010-05-18
Are you shutting off the computer abruptly?  The locate command needs a long time to index all of the files on your machine for a new install.  If you don't leave your machine running for a while (several hours) then it's possible that the locate indexing never gets finished.  What other drives are on this system?

The old mlocate files could be leftovers from interrupted indexing with previous installs.

---

### Post by lmicu on 2010-05-18
> **tgalati4 said:**
> Are you shutting off the computer abruptly?  The locate command needs a long time to index all of the files on your machine for a new install.  If you don't leave your machine running for a while (several hours) then it's possible that the locate indexing never gets finished.  What other drives are on this system?

The old mlocate files could be leftovers from interrupted indexing with previous installs.

I never shout down the computer, I mean if I did it once was couple of months ago when I had a crash. But that is pretty much the only time I can remember. I usually put it on stand by or hibernate.

I have only one hard disk on the computer but I have a ssh fs on the server that I load once in a while and leave it like that. Could that be the issue ... hmmmmm

PS: also when i want to unmount the sshfs (I usually have 3 paths mounted) I can unmount two just fine but the third (who is the home directory on the server) it never get unmounted, I get some errors and I have to use the lsof to find the PID and kill it and only then I can unmount it.

---

### Post by john newbuntu on 2010-05-18
fuse.sshfs was added recently to PRUNEFS in /etc/updatedb.conf.  This should have excluded sshfs lookups.  I am wondering if you need to tweak this file and add your sshfs mountpoint to PRUNEPATHS.
[https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/371749](https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/371749)

---

### Post by tgalati4 on 2010-05-19
True, otherwise, locate will try to index entire filesystems that are mounted via FUSE.  This would be a bug or a feature depending on how annoying or useful this condition is for you.

---

### Post by lmicu on 2010-05-26
Ok, I added fuse.sshfs in to PRUNEFS in /etc/updatedb.conf then I mounted the sshfs and it is looking good, no more 64GB of log files. 

Thank you guys!

PS: I will make it solved in a week, just to be sure this is actually working.

---

### Post by tgalati4 on 2010-05-26
When you think about it, isn't google just a large mlocate database?

---

### Post by linas on 2013-05-03
FYI, I've got a 3-4 year-old version of redhat (well, centos, actually) with the same problem (33GB worth of mlocate.db.* files with todays timestamp).  There's no fusefs on this system, fuse.glusterfs and gfs and gfs2 are already in /etc/updatedb.conf ... investigating.

---

### Post by overdrank on 2013-05-03
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

