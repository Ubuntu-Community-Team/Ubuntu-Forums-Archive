---
title: "Drive Scrubber"
date: 2011-10-22
forum: General Help
---

### Post by erbad on 2011-10-22
I have a number of hard drives that I need to scrub of data before I sell them.

Is there any utility available on Ubuntu that would securely wipe these drives so that no previous data could be recovered.

Thank you

---

### Post by critin on 2011-10-22
Did you Google it?  From what I've learned, data can almost always be recovered if someone seriously wants to.  I've seen ads for complete cleaning though--paid apts.

I think g-parted allows multiple wipes and writeovers.  Most people don't care what's been on the drive before and won't bother trying to recover it.

It's available from Software Center or Synaptic.  Some versions of Ubuntu keep it as a default after installation.

critin

---

### Post by gsmanners on 2011-10-22
I think I would probably use [DBAN]("http://www.dban.org/"), though whether it *really* works is anyone's guess. :D

---

### Post by WorMzy on 2011-10-22
dd is all you need, imo.

e.g.
```
sudo dd if=/dev/zero of=/dev/sda
```

will completely fill sda with zeroes.

or

```
sudo dd if=/dev/urandom of=/dev/sda
```

will fill sda with random garbage.

---

### Post by erbad on 2011-10-22
> **gsmanners said:**
> I think I would probably use [DBAN]("http://www.dban.org/"), though whether it *really* works is anyone's guess. :D

Dban was the one I was thinking of myself, but I was questioning how secure it is.

---

