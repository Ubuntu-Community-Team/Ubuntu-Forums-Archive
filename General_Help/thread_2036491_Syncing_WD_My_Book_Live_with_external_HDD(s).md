---
title: "Syncing WD My Book Live with external HDD(s)"
date: 2012-08-02
forum: General Help
---

### Post by Shadius on 2012-08-02
Hey everybody! :)

I have a WD My Book Live and I have a few external HDDs. What I want to do is to put the data from the external HDDs to my WD My Book Live. I'd also like to have it setup so that my WD My Book Live only syncs newly added files from the external HDD and/or updates any changes that I've made to the files on the external HDD. 

So say I add a file to the external HDD, the WD My Book Live would recognize that a new file has been added and add it to itself, or if a file has been deleted, that file would no longer be in the WD My Book Live. If I change a filename or some file property, it would reflect in the WD My Book Live. 

Is there a way to do this?

---

### Post by zero2xiii on 2012-08-02
Hay,

Have a look into [rsync]("http://en.wikipedia.org/wiki/Rsync").

Here is a nice tutorial I just happen to pass by:
[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

I assume there are other options, but as far as I know rsync is by far the most popular choice :)

EDIT:
Just saw this on the wiki:
[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)
Might help a bit if you do not like the CLI path.

Cherz

---

### Post by Shadius on 2012-08-02
> **zero2xiii said:**
> Hay,

Have a look into [rsync]("http://en.wikipedia.org/wiki/Rsync").

Here is a nice tutorial I just happen to pass by:
[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

I assume there are other options, but as far as I know rsync is by far the most popular choice :)

EDIT:
Just saw this on the wiki:
[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)
Might help a bit if you do not like the CLI path.

Cherz
Thank you, and thank you especially for providing the GUI method.

---

