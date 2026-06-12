---
title: "df question"
date: 2009-09-21
forum: General Help
---

### Post by bonfire89 on 2009-09-21
Hey all,

could someone please explain how this output from "df -h" makes sense


```
/dev/mapper/vg0-lvol0       6.1T  5.8T     0 100% /home
```


6.1/5.8 != 100%


is this an error? is there a fix? or is this the way it is supposed to happen?


thanks

---

### Post by badger_fruit on 2009-09-21
> **bonfire89 said:**
> could someone please explain how this output from "df -h" makes sense

No we can't .. because it doesn't!

What OS/version is this you're using?

I just ran df -h on my 9.04 system (kernel 2.6.28-15-generic) and it's correct.

What's the version of df you're using (df --version)?

Mine reports: df (GNU coreutils) 6.10

... and on my suse machine 6.11 df, kernel 2.6.25.20-0.4-pae

---

### Post by bonfire89 on 2009-09-21
```
me@dude:~$ df --version
df (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Torbjorn Granlund, David MacKenzie, and Paul Eggert.
```


:/ strange it is a bit of a problem because I was expecting another 200gigs, and now I have no room to write. heh

---

### Post by P4man on 2009-09-21
I remember reading somewhere that you can only use 95% of an Ext2/3/4 volume. That would be the "price" you pay for never having to defragment it.

---

### Post by P4man on 2009-09-21
actually more info and a possible "fix" here:
[http://ubuntuforums.org/showthread.php?t=1270762](http://ubuntuforums.org/showthread.php?t=1270762)

---

### Post by badger_fruit on 2009-09-21
> **P4man said:**
> I remember reading somewhere that you can only use 95% of an Ext2/3/4 volume. That would be the "price" you pay for never having to defragment it.


That would make sense, 5.8 is 95.08% of 6.1 = 100% used in EXT's eyes.

---

### Post by bonfire89 on 2009-09-21
Oh, very interesting! Well, considering this isn't my root partition, I should be able to reduce that reserved space.

Thanks!

---

