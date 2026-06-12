---
title: "Terminal help please"
date: 2010-06-30
forum: General Help
---

### Post by Abu Azzubair on 2010-06-30
I've just downloaded Wine using Terminal

Note: Instructions were on [http://www.winehq.org/download/](http://www.winehq.org/download/) then **[Download Ubuntu packages]("http://www.winehq.org/download/deb")**  ([http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)), and I just followed the instructions...etc

But Wine was somethin like 108 MB I think!!

I need to check how much memory space I got on my computer since it's a dual boot system (...etc), and something like that would take a lot of space

Basically

What's the command to that lets you see how much space left on the hard drive please?
**[]("http://www.winehq.org/download/deb")**

---

### Post by GreenN00b on 2010-06-30
```
df -h
```

---

### Post by akelsall on 2010-06-30
You can also use gparted to get a look at how much is being used up in each partition:

sudo gparted &

---

### Post by howefield on 2010-06-30
Graphical applications are better called with gksudo, not sudo.

---

### Post by SoupFlies on 2010-07-01
> **howefield said:**
> Graphical applications are better called with gksudo, not sudo.

I am curious, why is this? I have noticed this specific comment many times throughout many boards today, and I am finally to the point where I must ask, when using graphical applications, why is gksudo better for calling them, than regular ol' sudo

---

### Post by oldos2er on 2010-07-01
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Abu Azzubair on 2010-07-01
Hey thanks a lot everyone, really appreciated :)

> [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Very much appreciated for this link [oldos2er]("http://ubuntuforums.org/member.php?u=338320"),that showing me and everyone (mostly newbies like myself Lol) a new branch/slightly new branch in Terminal :)

---

