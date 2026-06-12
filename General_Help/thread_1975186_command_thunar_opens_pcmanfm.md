---
title: "command thunar opens pcmanfm"
date: 2012-05-07
forum: General Help
---

### Post by ohnonot on 2012-05-07
hello,
i think i did this myself but i can't find it anymore.
:oops:
i think i created a link at some point that does that, because it's the only way to get xfce places plugin use something else then thunar.

now i'm trying to use a different fm and tried to locate all files called thunar but there's only 2 (in /usr/bin and /usr/sbin) and neither looks like a link. creating a new link ```
sudo ln /usr/bin/spacefm /usr/bin/thunar
```doesn't give an error message, but doesn't seem to show any result
:confused:
still, when i type thunar it opens pcmanfm.
the only way to actually access thunar is to type Thunar.
i'm confused.
any help appreciated, thanx.

[edit: some searching tells me i should use symbolic links. this code: sudo ln -s /usr/bin/spacefm /usr/local/bin/thunar -v did the trick. however it seems that those hard links - see above - are still there somewhere? how can i remove them?]

---

### Post by Toz on 2012-05-07
Try reinstalling thunar:
```
sudo apt-get install --reinstall thunar
```

---

### Post by brainwash on 2012-05-07
> **ohnonot said:**
> still, when i type thunar it opens pcmanfm.
the only way to actually access thunar is to type Thunar.
Take a look at this:
```
brainwash@local:~$ ll /usr/bin/Thunar
-rwxr-xr-x 1 root root 768436 Apr  4 19:08 /usr/bin/Thunar*
brainwash@local:~$ ll /usr/bin/thunar
lrwxrwxrwx 1 root root 6 Apr 17 17:46 /usr/bin/thunar -> Thunar*
```

---

### Post by ohnonot on 2012-05-10
> **brainwash said:**
> Take a look at this:
```
brainwash@local:~$ ll /usr/bin/Thunar
-rwxr-xr-x 1 root root 768436 Apr  4 19:08 /usr/bin/Thunar*
brainwash@local:~$ ll /usr/bin/thunar
lrwxrwxrwx 1 root root 6 Apr 17 17:46 /usr/bin/thunar -> Thunar*
```eggzaggly!
it seems i had overwritten that (thunar with a small t) with a hard link (although i'm still not quite sure what that means).
bravely, i deleted it and placed a symlink to Thunar in /usr/local/bin/thunar.

thanks for the help.

solved, unless someone wants to elaborate on links.
it seems like "hard" links are not recognizable as links - i only found out by specifically executing /usr/bin/thunar, which opened pcmanfm.

---

