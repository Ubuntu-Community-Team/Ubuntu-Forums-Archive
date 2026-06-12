---
title: "Comman to copy files in directory created within 2 hours."
date: 2010-04-22
forum: General Help
---

### Post by FeraTech on 2010-04-22
Is there a simple command to copy files that have been created within the past 2 hours?

I've been looking through the man pages for 
unison
rsync
find
cp

and I can't find anything I'm looking for.

All I need is a simple command.

```
Copy folder a to b if created < 2 hours.
```

---

### Post by BobvanderPoel on 2010-04-22
1. Linux/Unix doesn't track create times. You'll have to be happy with access and modified times.

2. The "find" command is what you want to use. Read the manual page for examples.

Hope this helps.

---

### Post by cgb on 2010-04-22
Are you trying to basically keep a folder constantly backed up every two hours with any changes copied over?  If so a simple rsync script running every two hours will do the trick...

---

### Post by FeraTech on 2010-04-22
No it's a bit more complicated than that....

I'm looking through the find manual right now and it looks like I need to find files modified in the last day.


What I am trying to do is have pictures on the server that are always there. However, new ones uploaded will get downloaded onto my desktop. Then once I am done I want to be able to delete the pictures without having them deleted on the server or the server uploading all the ones I deleted already.

With rsync there are only two real options.

1. Keep both directories in sync. ie, a deleted file means it is deleted on both.

2. One way sync means a deleted file is immediately replaced by the copy from the server.

---

### Post by cgb on 2010-04-23
Ah, yes...  A little different then what I was thinking you were trying to do but the find command should then be able to do what you are looking for..

---

