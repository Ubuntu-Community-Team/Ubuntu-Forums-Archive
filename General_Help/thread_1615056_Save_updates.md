---
title: "Save updates?"
date: 2010-11-06
forum: General Help
---

### Post by Fracta on 2010-11-06
I was wondering if there was a way for me to get all the updates off my ubuntu and save it as an archive or image or something, so that when I do a reinstall, I don't need to download them all again?
Is there a directory where all the repository downloads are saved before they are installed?
It would be a huge help, because I know other people who would like ubuntu but can't download the updates, mostly due to internet costing tons over here.

---

### Post by Elfy on 2010-11-06
They are in 

/var/cache/apt/archives

Save them to whatever you want - on the other machines run nautilus as root and copy them in then do and update.

```
gksudo nautilus /var/cache/apt/archives
sudo apt-get update
```

You might still have to get the odd update for particular machines - but the majority should be ok.

---

### Post by Fracta on 2010-11-06
Thats perfect! thanks tons. Saves SO much time. And yeah I realise there will be some machine specific updates. Thats the way it goes.

---

### Post by Fracta on 2010-11-17
Ok I just reinstalled ubuntu and copied over the archives folder (and changed permissions) but it looks like nothing changes. Update Manager still says I need to download 156 updates and I am sure I can't have missed that many over the last week.
I did run the sudo apt-get update.
How can I get all the things I have already downloaded to install?

And I can install from the archives by double clicking on the files, but there is quite a few of them in there and it would take a LONG time.

---

