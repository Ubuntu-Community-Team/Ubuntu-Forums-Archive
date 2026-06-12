---
title: "Dirctory d:\ doesnt exist - dosbox"
date: 2010-05-07
forum: General Help
---

### Post by SimplySimon... on 2010-05-07
Hi there!

So, i'm running ubuntu 10.04 and windows vista on my laptop and I installed Dos box on ubuntu quite some time ago, when i went to mount my d drive (like i usually do in windows) I got the error message "directory D:\ does not exist" i tried to fix it myself but i gave up because it wasnt that important. A while later i read on a webpage that "Linux does     not employ the concept of drive letters" so i thought this must be the reason for this error message but why would there be dosbox for linux if that was the case? And is there a fix?

Help is much appreciated, thanks  ;)

---

### Post by rCXer on 2010-05-07
* First you need to make sure your Windows partition is mounted.  Just click on it from the "Places" menu.

* Then browse to where your dos programs are usually kept and note the path e.g. "/media/sda1/DosGames/"

* In dosbox simply type
```

mount d "/media/sda1/DosGames/"

```

---

### Post by SimplySimon... on 2010-05-10
Thank you soooo much!!! :lol:

---

