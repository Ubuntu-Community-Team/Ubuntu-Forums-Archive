---
title: "Two backup solutions: one-way sync and off-site incremental"
date: 2009-11-14
forum: General Help
---

### Post by karmakowski on 2009-11-14
Hello, 

I run into some file system troubles recently which almost caused a serious data loss. That got me thinking and I figured out I could use some backup solution, at least for the most important and irreplaceable files. 

I have two computers -- laptop with Ubuntu and always-on home server with FreeBSD -- containing "critical" data and a third one (old desktop, also with Ubuntu :) I can use for storage of less important files. 

**One way sync, master/slave copy**
The less important stuff first. I would like to copy my whole home directory from the server to the desktop (they even have disks of the same size) but not with some fancy sync preserving erased files and all -- whatever is deleted on the server should be deleted from the desktop during sync, whatever changed should be changed without keeping any old versions, but preferably without copying over the stuff that already has been copied or just moved, let it just be moved in that case. I will be doing that over fast, home network but still. Simply coping it takes ~10 hours. 
Is this possible with rsync somehow? Do I need another tool? If so, which? 

**Off-site, incremental, encrypted and signed backup**
I am looking for a possibly cheap, secure and efficient way to backup my more important files (saved passwords and settings, photos, documents, projects,, more photos e-mails, personal websites...) in a distant location. Two solutions I consider would be:
a) Duplicity + S3, maybe using Deja Dup for convenience. If I used the calculator from Amazon right it would cost about $60 for 30GB backed up over the year, reasonable. 
b) External hard drive on which I would simply copy everything and drop off at my parents' house or some other relatively safe place. I could even use duplicity just the same. 

What would you recommend? What solution do you use for sensitive backups?

---

### Post by XCan on 2009-11-14
For you first question, yes, it is very possible to do it using rsync. You can either access your stuff remotely using ssh, or if you prefer the rsync deamon, or if you must, by mounting a shared drive. This is what I run when I rsync down my workstation 
```

rsync -avz --progress --delete --rsh="ssh -p1234" user@123.123.123.123:/home/worker /home/me/workerhomeback

```

---

