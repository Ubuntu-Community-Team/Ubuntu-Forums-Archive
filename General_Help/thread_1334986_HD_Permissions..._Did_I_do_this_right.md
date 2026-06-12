---
title: "HD Permissions... Did I do this right?"
date: 2009-11-23
forum: General Help
---

### Post by FootySr on 2009-11-23
Hello Everyone!

I have an internal HD that I just want to use to back a few things up now and then. Mostly my music and photos. At any rate I did a fresh install of 9.10 on release but noticed I couldn't actually read/write to the internal hard drive since it was owned by the root.

I did do some searching on this and there seemed to be more than one way to do it. I opened terminal, tossed in a "gksudo nautilus" mounted the internal drive and changed the owner and group permissions to match that of my home folder.

I was able to copy the 250 CDs I just ripped to ogg last week so everything seems to work as it should. 

Any down sides to what I've done here or is my OCD kicking in? ;)

Thanks,

Jake

---

### Post by mgol on 2009-11-23
I would do the same. ;) Of course if You would rather have free access to everybody for this HDD, You'd better change permissions so that everyone has read-write permissions.

(I assume the drive has one of *nix filesystems on it).

---

### Post by Andreas1 on 2009-11-23
since it seems to be *your* data you could change the ownership:

```
sudo chown -R 1000:1000 [mountpointofyourhd]
```

(1000 is your user id, you could also write footysr:footysr if that is your name)

---

### Post by FootySr on 2009-11-23
Thanks Guys!

Both internal drives are formatted ext4 and I'm the only one on this computer.

Jake

---

