---
title: "Cannot run dropbox"
date: 2009-07-28
forum: General Help
---

### Post by samden on 2009-07-28
I have installed dropbox by downloading and installing the .deb file from their website:
[http://www.getdropbox.com/downloading?os=lnx](http://www.getdropbox.com/downloading?os=lnx)

I logged out, logged back in again, and started Nautilus. The nautilus-dropbox extension should have started at this point, however I see no change to nautilus.

I also tried running "killall nautilus" and restarting nautilus - no luck.

I added the dropbox repositories and ran sudo apt-get install nautilus-dropbox. This told me it was already the latest version.

Any ideas why this just doesn't seem to run for me?

---

### Post by eriqjaffe on 2009-07-28
Make sure that dropbox is set to start up automatically.  In my Startup Applications, I have a Dropbox entry that runs this:

```
dropbox start -i
```

---

### Post by samden on 2009-07-28
Thanks for that. Managed to get it to go by running dropbox start -i, but you are right, I'll have to add it to my startup apps.

It's a shame it didn't run automatically, but it works well now, I'd recommend it to others from what I've seen so far.

---

### Post by magmon on 2009-07-28
It didn't start up automatically for me after my first restart either. I had to go to applications -> Internet -> Dropbox, it installed the daemon and worked from there on.

---

### Post by xjgnsdof on 2009-09-20
> **eriqjaffe said:**
> Make sure that dropbox is set to start up automatically.  In my Startup Applications, I have a Dropbox entry that runs this:

```
dropbox start -i
```

Thanks. That works on my Ubuntu Server Edition 9.04 PC.

---

