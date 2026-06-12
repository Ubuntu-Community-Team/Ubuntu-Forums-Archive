---
title: "&quot;System Program Problem Detected&quot;"
date: 2012-09-15
forum: General Help
---

### Post by bower4311 on 2012-09-15
I have been getting this message with both Ubuntu 12.04LTS installs on my computer. It came back now, about the same time my sound started skipping in youtube videos and in spotify.I already re-installed once to try and get rid of it.

Screen shots are attached.

---

### Post by kaytrance on 2012-09-15
Very much sounds like a bad sectors on HDD, you might want to check for ones.

---

### Post by bower4311 on 2012-09-15
How would I go about doing that?

---

### Post by kaytrance on 2012-09-15
> **bower4311 said:**
> How would I go about doing that?
There are tons of ways, like [this]("http://linuxpoison.blogspot.com/2008/01/howto-check-disk-drive-for-errors-and.html") or [this]("http://bredsaal.dk/checking-a-harddrive-for-bad-sectors-on-ubuntudebian") or even [this]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/").

---

### Post by bower4311 on 2012-09-15
I ran the ten minute check from disk utility and nothing showed up.

I get this when I try badblocks, I don't know much about Ubuntu.

SS attached.

---

### Post by zvacet on 2012-09-15
I have same problem and I run test with Disc Utility.It say no badblocks.Should I try other methods with live CD,because I want to check root partition?

---

### Post by zvacet on 2012-09-16
I tried with 

```
 sudo badblocks -v /dev/sda1 > bad-blocks
```

and there is no bad blocks.I s it possible that message we get is just bug in system?

---

### Post by bower4311 on 2012-09-16
I'm not getting the message anymore so maybe it's fine.

---

