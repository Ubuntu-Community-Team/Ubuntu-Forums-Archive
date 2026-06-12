---
title: "Cant delete ubuntu?"
date: 2010-03-24
forum: General Help
---

### Post by kamilii on 2010-03-24
I was having to many problems with it and decided to delete it so i go to  the uninstaller and it says an error occurred:invalid argument 

For more information, please see the log file: c:\docume~1\locals~1\temp\wubi-0.10ubuntu1-rev160.log 

I tried to find what log it was talking about but couldnt find it help?

---

### Post by bcbc on 2010-03-24
> **kamilii said:**
> I was having to many problems with it and decided to delete it so i go to  the uninstaller and it says an error occurred:invalid argument 

For more information, please see the log file: c:\docume~1\locals~1\temp\wubi-0.10ubuntu1-rev160.log 

I tried to find what log it was talking about but couldnt find it help?
Try this: [https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

---

### Post by kamilii on 2010-03-24
Uh cant get past the first step  try to remove wubildr it says cannot delete wubildr the file or directory is corrupt and unreadable

---

### Post by bcbc on 2010-03-24
> **kamilii said:**
> Uh cant get past the first step  try to remove wubildr it says cannot delete wubildr the file or directory is corrupt and unreadable

Try running chkdsk:
```
chkdsk /r
```

---

### Post by kamilii on 2010-03-24
Said it deleted it but its still there

---

### Post by bcbc on 2010-03-24
> **kamilii said:**
> Said it deleted it but its still there

What happened when you ran chkdsk?

---

### Post by kamilii on 2010-03-24
It loaded the comand prompt and it said it was scanning files after a while when it got to like 70% it said it deleted wubildr

---

### Post by bcbc on 2010-03-24
> **kamilii said:**
> It loaded the comand prompt and it said it was scanning files after a while when it got to like 70% it said it deleted wubildr

Ok - I'm not sure what's up with that - did you try booting into repair mode and dropping to the command line to run chkdsk?
Were you able to remove the \ubuntu\disks\root.disk file? That's the big one, so you can reclaim the space.

---

### Post by kamilii on 2010-03-24
Was able to delete the root file going to try to boot into repair mode

---

### Post by kamilii on 2010-03-24
Yay The thing got the file uncorrupted and I was able to use the

---

