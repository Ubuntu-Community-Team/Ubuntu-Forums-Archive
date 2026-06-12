---
title: "Calling all rsync pros"
date: 2010-11-17
forum: General Help
---

### Post by b4t3m4n on 2010-11-17
I need a bash script for rsync to sync some directories on my laptop with my server at home via SSH.  I am asking for help because I always get it confused and I don't want to lose my data.

Basically, if I change something on my laptop, I want it to be added to both the server and laptop, but I also want it added to the laptop if I change something on the server.  Basically no file removal.

Also, say I edit a document on my laptop, will rsync realize which edit is newer and update it appropriately?

Lastly, I want it as a bash script for several different directories.  I am crappy at bash scripts.  How would one make a script that executes a command and waits for that command to finish before executing the next.

---

### Post by CharlesA on 2010-11-17
It won't do it automagically, if that's what you want.

You'd probably be better off looking into something like Unison instead of rsync.

Do you use yer laptop in one place all the time? If so, you'd probably be better off using NFS or SSHFS to access the files on the server and just keeping everything there.

---

### Post by b4t3m4n on 2010-11-17
Unison looks interesting, surprised I have never heard of it before tbh.

---

### Post by CharlesA on 2010-11-17
That would probably be the best way to go about it.

The way I do it is I just access files from the server and sftp them to/from the machine if working remotely. Makes it easier to keep everything in sync.

---

