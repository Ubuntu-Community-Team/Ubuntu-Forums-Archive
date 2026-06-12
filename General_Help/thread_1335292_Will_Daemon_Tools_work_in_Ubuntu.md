---
title: "Will Daemon Tools work in Ubuntu?"
date: 2009-11-23
forum: General Help
---

### Post by jras20 on 2009-11-23
Will Daemon Tools work in Ubuntu or a program like it?  I'd like to use it for tools.
Thanks.

---

### Post by undecim on 2009-11-23
If I'm not mistaken, Daemon tools allows you to create and mount virtual disks in Windows?

You don't need daemon tools for that in Ubuntu. It does that stuff all on its own.

---

### Post by silentknyght on 2009-11-23
> **undecim said:**
> If I'm not mistaken, Daemon tools allows you to create and mount virtual disks in Windows?

You don't need daemon tools for that in Ubuntu. It does that stuff all on its own.

More specifically, if you have a disc image called "disc.iso" and want to mount it as "disc", try this at the command line:

```

sudo mkdir /media/disc

```

followed by
```

sudo mount disc.iso /media/disc -t iso9660 -o loop

```




When you're finished with it...

```

sudo umount /media/disc

```

followed by

```

sudo rmdir /media/disc

```

---

### Post by Cheesemill on 2009-11-23
Or to rip a disc to an iso file you can do:
```
dd if=/dev/cdrom0 of=file.iso
```

---

### Post by Cheesemill on 2009-11-23
I've just gone to the Software Centre and done a search for iso.

It looks like Furius ISO Mount might work for you (I've never tried it though).

Doing a search in the Software Centre should always be your first stop, it took me seconds to find that program for you :KS

---

### Post by shaggy999 on 2009-11-23
It should be noted that mounting only works for basic images like iso. It won't work with alcohol/blindwrite/clonecd/etc images like daemon tools does. There are tools available that will convert those specialized images to iso, but they will strip out the extra data that those image formats include like subchannel data and such.

---

