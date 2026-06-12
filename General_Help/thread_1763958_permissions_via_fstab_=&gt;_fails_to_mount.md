---
title: "permissions via fstab =&gt; fails to mount"
date: 2011-05-21
forum: General Help
---

### Post by Gakumerasara on 2011-05-21
I'd like to have a hard drive partition mount within my home folder as backup/, but every time I restart the computer in question, I get a nondescript error message.

```
UUID=xxxxxxxx-e44c-4723-bbbf-fa83047ac43b /home/xxx/backup      ext4    defaults,umask=000,uid=1000,gid=1000    0 0
```gives me the error while

```
UUID=xxxxxxxx-e44c-4723-bbbf-fa83047ac43b /home/xxx/backup      ext4
```works fine (aside from the permissions)

I've checked that the uid/gid are correct.  What am I doing wrong?  Thanks,

---

### Post by coffeecat on 2011-05-21
What was the nondescript error message? Even if nondescript, it might contain a clue.

I think something is missing from your second example. Did you mean...

```
UUID=xxxxxxxx-e44c-4723-bbbf-fa83047ac43b /home/xxx/backup      ext4      defaults   0 0
```

?

If so, one way round this is to us the line I've posted and change ownership and permissions of the partition filesystem while it is mounted. Mount it with the line I have posted and then:

```
sudo chown xxx: /home/xxx/backup
sudo chmod 777 /home/xxx/backup
```

Obviously, substitute xxx for whatever it should be, and the trailing colon in the first command is correct - it tells chown to use your default group. Those two commands actually act on the root of the filesystem, not on the mountpoint, so will stick if you ever change the mountpoint. Your permissions issues should then melt away.

As far as your original question is concerned, I don't know. Your first fstab line looks OK, unless the nondescript error is telling us something.

One last point - you might want to have "0 2" in the last two fields, not "0 0".

---

### Post by Gakumerasara on 2011-05-21
> **coffeecat said:**
> What was the nondescript error message? Even if nondescript, it might contain a clue.

The error is:
"An error occurred while mounting /home/xxx/backup
Press S to skip mounting or M for manual recovery"
Each of the partitions gives the same error (with different mount locations).  This same error appears whether I use "0 0" or "0 2" as you suggested.

> **coffeecat said:**
> I think something is missing from your second example. Did you mean...
```
UUID=xxxxxxxx-e44c-4723-bbbf-fa83047ac43b /home/xxx/backup      ext4      defaults   0 0
```
?
Yes and no.  I know your example is the correct way, but leaving out the last 3 columns uses defaults for the same effect.

> **coffeecat said:**
> If so, one way round this is to us the line I've posted and change ownership and permissions of the partition filesystem while it is mounted. Mount it with the line I have posted and then:

```
sudo chown xxx: /home/xxx/backup
sudo chmod 777 /home/xxx/backup
```

Obviously, substitute xxx for whatever it should be, and the trailing colon in the first command is correct - it tells chown to use your default group. Those two commands actually act on the root of the filesystem, not on the mountpoint, so will stick if you ever change the mountpoint. Your permissions issues should then melt away.

edit: That solved the problem; thanks!

---

### Post by coffeecat on 2011-05-21
> **Gakumerasara said:**
> Yes and no.  I know your example is the correct way, but leaving out the last 3 columns uses defaults for the same effect.

That's a new one on me. Thanks!

> **Gakumerasara said:**
> edit: That solved the problem; thanks!

Glad it worked. It seems to be a little understood phenomenon. Most people think you are chmodding or chowning the mountpoint or files already in the filesystem rather than the filesystem itself. I find it much easier than fiddling about with mount options.

---

