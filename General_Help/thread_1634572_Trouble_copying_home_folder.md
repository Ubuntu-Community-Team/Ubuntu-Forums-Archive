---
title: "Trouble copying home folder"
date: 2010-11-30
forum: General Help
---

### Post by Berethorn on 2010-11-30
I'm trying to copy my entire /home folder to an external hard drive in prep for a fresh install. The /home folder is about 300GB because there's a lot of video and photos on it.

Last night I gksudoed Nautilus and manually dragged the /home folder over to the external to copy. It worked on that throughout the night with only a handful of errors on random files (I clicked skip every time). But when I checked, I found a few folders in /home/user had not copied - random folders, no apparent pattern. I copied those over manually, checked the Contents with Nautilus: both /home folders now showed almost exactly the same number of files. Great?

No - I later noticed that some, not most but some, of the *hidden* folders in the /home/user folder were also not copied.

So.. does Nautilus not include hidden folders when calculating its number of files?

To make sure I get everything transferred, I'm doing this now:

```
sudo cp -a -v -u /home/user /media/Elements/UBUNTU/home/
```

Should that "fill in the cracks"? Thanks for any help, I didn't think copying files would be such a headache, but then I should have used the command line in the first place. :(

---

### Post by Dans564 on 2010-11-30
This isn't exactly fixing your problem but i guess its a work around.  This sort of thing has happened to me too.  Instead use a live cd to do the backup/copying.  This worked for me.

---

### Post by Berethorn on 2010-11-30
Yeah, that's what I should do in the future, not let the OS get in the way of copying. :-\

---

### Post by Dans564 on 2010-11-30
yea kind of rudimentary, but it worked nonetheless.

---

