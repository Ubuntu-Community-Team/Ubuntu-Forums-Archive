---
title: "Question regarding rsync"
date: 2009-07-01
forum: General Help
---

### Post by enigmaniac23 on 2009-07-01
I am using rsync to keep my music synced between my Hard Drive and my external usb.  For some reason, there are about 35 files out of about 4900) that are deleted and re-copied every time I run rsync.  It seems to be the same files every time.  I'm not sure that it's an actual problem, because it seems to be re-copying the files to the external each time, but I'd rather it not have to do that, since the files aren't changing.  I have run rsync back to back with no changes to the files at all, and this consistently happens.  If I run the command with the --dry-run option, it tells me that it is not going to transfer any files.  Then, I run it again without the --dry-run and sure enough, it transfers the 35 files.  I'm not extremely familiar with rsync, but I'm running the following:

```
rsync -v -r -q --size-only --delete --exclude=".*" --stats /home/user/Music /media/USB/
```

I see the following in the stats
*deleting   Music/3/3 Doors Down/Away from the Sun/01 - When I'm Gone.mp3
>f+++++++++ Music/3/3 Doors Down/Away From The Sun/01 - When I'm Gone.mp3

---

### Post by colau on 2009-07-01
> **enigmaniac23 said:**
> I am using rsync to keep my music synced between my Hard Drive and my external usb.  For some reason, there are about 35 files out of about 4900) that are deleted and re-copied every time I run rsync.  It seems to be the same files every time.  I'm not sure that it's an actual problem, because it seems to be re-copying the files to the external each time, but I'd rather it not have to do that, since the files aren't changing.  I have run rsync back to back with no changes to the files at all, and this consistently happens.  If I run the command with the --dry-run option, it tells me that it is not going to transfer any files.  Then, I run it again without the --dry-run and sure enough, it transfers the 35 files.  I'm not extremely familiar with rsync, but I'm running the following:

```
rsync -v -r -q --size-only --delete --exclude=".*" --stats /home/user/Music /media/USB/
```

I see the following in the stats
*deleting   Music/3/3 Doors Down/Away from the Sun/01 - When I'm Gone.mp3
>f+++++++++ Music/3/3 Doors Down/Away From The Sun/01 - When I'm Gone.mp3

Describe your problem specifically.

---

### Post by enigmaniac23 on 2009-07-01
The problem was simply that rsync was copying files over that it didn't need to copy each time.  I found out that this was because of some folders that were duplicated.  They were duplicated but one folder had uppercase and the duplicate was lower case.  I cleaned up the files, removed them from the external drive and ran rsync again and now it's working perfectly.

---

### Post by colau on 2009-07-02
> **enigmaniac23 said:**
> The problem was simply that rsync was copying files over that it didn't need to copy each time.  I found out that this was because of some folders that were duplicated.  They were duplicated but one folder had uppercase and the duplicate was lower case.  I cleaned up the files, removed them from the external drive and ran rsync again and now it's working perfectly.
You can also use grsync.
```

sudo aptitude install grsync

```

---

