---
title: "Can't figure out how to write to HFS+ (journal disabled) external drive"
date: 2009-10-16
forum: General Help
---

### Post by domokunrox on 2009-10-16
I tried to follow some other instructions, but alas I couldn't get the grip of it. I ride the Linux short bus. Sorry.

Heres the issue. I need to backup some data here on Linux onto my WD eternal drive. Its HFS+ (Journal disabled), but I can't get it to write. Drive is currently mounted /media/Paul C

An almighty command to force it to be writable would be great. I'm dreading having to back up all my data elsewhere to format the drive from scratch. I appreciate the help. Thanks.

---

### Post by beastrace91 on 2009-10-16
Linux cannot write to HFS+ - format the drive to a non-crappy file system. Apple FS is decently retarded :/

EDIT: Check it- [http://www.engadget.com/2008/02/05/linus-torvalds-calls-apples-file-system-utter-crap/](http://www.engadget.com/2008/02/05/linus-torvalds-calls-apples-file-system-utter-crap/)

~Jeff

---

### Post by domokunrox on 2009-10-16
wow, omg, I got it to work somehow. My brother called me back and told me to do

```
gksudo nautilus
``` 

then navigate to my drive and edit the permissions to my user and it worked!

Problem solved!

---

### Post by beastrace91 on 2009-10-16
Really? I could have sworn my Ubuntu system wouldn't write the an HFS+ formatted drive (root or otherwise). At any rate I would still recommend formatting the drive to ntfs or extX

Sorry for being mistaken.

~Jeff

---

