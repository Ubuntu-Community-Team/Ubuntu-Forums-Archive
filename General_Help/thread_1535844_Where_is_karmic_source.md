---
title: "Where is karmic source"
date: 2010-07-21
forum: General Help
---

### Post by baltazar3 on 2010-07-21
Hi

Where is the official, recommended, vanilla source for karmic desktop?
I want to install tuxonice. To be able to install I have to patch and recompile the source. But I cant find it. There are only linux-headers in /usr/source.

uname -a returns: 2.6.32-22-generic
But I cant find this version on kernel.org.

I tried an older version, 2.6.31-12, but when I booted it I got wrong (lower) screen resolution. I guess because my nvidia card isnt supported. Is there anything special I have to do to make this work after recompile. The kernel Im running now, that got installed with cd works as it should.

---

### Post by howefield on 2010-07-21
> **baltazar3 said:**
> Where is the official, recommended, vanilla source for karmic desktop?

Is this what you are after ?

[http://cdimage.ubuntu.com/releases/9.10/release/source/](http://cdimage.ubuntu.com/releases/9.10/release/source/)

---

### Post by sandyd on 2010-07-21
> **baltazar3 said:**
> Hi

Where is the official, recommended, vanilla source for karmic desktop?
I want to install tuxonice. To be able to install I have to patch and recompile the source. But I cant find it. There are only linux-headers in /usr/source.

uname -a returns: 2.6.32-22-generic
But I cant find this version on kernel.org.

I tried an older version, 2.6.31-12, but when I booted it I got wrong (lower) screen resolution. I guess because my nvidia card isnt supported. Is there anything special I have to do to make this work after recompile. The kernel Im running now, that got installed with cd works as it should.

install "linux-source" and look in /usr/source again.

---

