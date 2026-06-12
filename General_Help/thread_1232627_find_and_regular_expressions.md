---
title: "find and regular expressions"
date: 2009-08-05
forum: General Help
---

### Post by Loetje on 2009-08-05
Hi,

I know this is completley off topic but since this is such a helpful community i thought i'd give it a shot:

I'm a almost complete noob and i'm trying to use find to search for all underlying folders in that have, let's say, 'beatles' in their name.

I've come up with this:

find ./ -name .*beatles.* -type d

This doesn't work (ofcourse).

Can anyone help?

---

### Post by wojox on 2009-08-05
Try that:
```
find -type d -name "beatles"
```

---

### Post by Loetje on 2009-08-05
> **wojox said:**
> Try that:
```
find -type d -name "beatles"
```
sorry, this doesn't work. It has to be anywhere in the name, so the folder can be 'Beatles - Yellow Submarine' or 'The Beatles - Yellow Submarine'

---

### Post by michy99 on 2009-08-05
```
find ./ -iname '*beatles*' -type d
```Note: -iname is case insensitive, whereas -name is case sensitive.

---

### Post by t0p on 2009-08-05
If you're looking in just the directories and subdirectories in /home, try

```
find /home -name '*beatles*'
```

If you want to look everywhere, how about

```
sudo find / -name '*beatles*'
```

There's a nice guide to using find [here]("http://www.codecoffee.com/tipsforlinux/articles/21.html").

---

### Post by Loetje on 2009-08-08
thanks for all the replies. I'm going with michy99's tip, it works exactly how i want.

---

### Post by andrew.46 on 2009-08-09
Hi t0p,

> **t0p said:**
> There's a nice guide to using find [here]("http://www.codecoffee.com/tipsforlinux/articles/21.html").

There will be a 'home-grown' Ubuntu version in place soon:

find - Ubuntu Community Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

I just need another week to finish it off...

Andrew

---

