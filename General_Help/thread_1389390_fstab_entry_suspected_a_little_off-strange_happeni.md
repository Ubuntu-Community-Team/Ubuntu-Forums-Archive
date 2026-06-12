---
title: "fstab entry suspected a little off-strange happenings with mounted drive"
date: 2010-01-24
forum: General Help
---

### Post by schwim on 2010-01-24
Hi there everyone,

I've got a weird problem.  I'm mounting two win shares via fstab.  The strange part is that most of the apps handle the data just fine, retrieving and saving data on the shares as they should.  Some apps however, don't treat the data as they should.  Two examples:

1) Gedit:  When saving a file on a win share, it states that it was unable to save.  When I check however, it did save the file and created the backup file.  <b>It was able to save even though it thought it didn't.</b>

2) Songbird: Although it used it for a week or so with no issue,  Songbird now doesn't even see the win share, stating it's not a valid location.  Rythmbox has been using the share just fine for three months as well as all other audio applications.

Initially, after just installing Karmic, both Gedit and Songbird worked properly, with gedit not throwing an error on save and Songbird using my win share.  After an early system update, things got a little weird in this respect.

here's one of my fstab entries:

```
//192.168.1.199/Websites /mnt/websites cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
```

If you see something I might be able to change that would resolve my issues, I would greatly appreciate it.

thanks,
json

---

### Post by schwim on 2010-01-25
So I'm clear, not a single suggestion, idea or observation from the world's largest and friendliest Ubuntu forum on the face of the earth?

thanks,
json

---

### Post by schwim on 2010-01-26
That's some top-notch support, Lou.

thanks,
json

---

