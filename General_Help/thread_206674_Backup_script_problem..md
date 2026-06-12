---
title: "Backup script problem."
date: 2006-06-30
forum: General Help
---

### Post by eddorey2k3 on 2006-06-30
Hi,

So i'm trying to create a COMPLETE archive of my hard drive, so that when I brak it I can just go back and restore it to it's current condition.

I found a script found on [http://www.hddsaver.com/content/26/index.html]("http://www.hddsaver.com/content/26/index.html")

To save you looking:

```
cd /
sudo tar cvpzf mybackup.tgz / --exclude=/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys

```

However. This doesn't seem to stop working. It archives the whole hard drive (Which takes forever, but i'm expecting it to, and produces a 50GB file) but then it seems to start trying to archive itself.

I've changed the original command slightly, so instead of it saying the above, it now reads:

```
cd /
sudo tar cvpzf **backup.tgz** / --exclude=/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys
```

So that the file name and the exclude match, but it still doesn't work.

Could it be the forward slash before the exclude that's not making it ignore it? If not, i'm really out of ideas >_>

Thanks.

---

### Post by xtacocorex on 2006-06-30
You should try PartImage. Here is a How-To for it: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) (Credit: aysiu)

I haven't used it, but aysiu's tutorial makes it look easy to use and seems to do what you want.

---

