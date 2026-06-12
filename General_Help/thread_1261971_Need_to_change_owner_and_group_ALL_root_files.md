---
title: "Need to change owner and group ALL root files"
date: 2009-09-09
forum: General Help
---

### Post by ultralame on 2009-09-09
I have a system that appears to be very messed up.

When I installed this one, with Ubuntu 6.x a few years ago, the root group was installed as "7root".  Things worked FINE for most of the time, until I upgraded to 8.10 and now 9.04.

The root group was created with gid 1010 at some point.

I have no idea why it was ever "7root", I assumed this was some new linux thing.  Now I search for that and google turns up nothing.

So I need to...

1) change all my 7root file properties to root.
2) Figure out what programs are running as 7root and fix that.

Etc

Can anyone tell me how to do this?

---

### Post by John Baptist on 2009-09-09
I have no idea why your groups are messed up. But you should be able to fix it like this:

First, create the real root group, if it doesn't already exist:

```

sudo addgroup --system --gid 0 root

```

Then, change all files from 7root to root:

```

sudo bash -c 'find / -group 7root -print0 | xargs -0 chgrp root'

```

That should work, although it might take a while.

Before you do that, though, you should probably post your /etc/group file here so we can see what happened.

---

