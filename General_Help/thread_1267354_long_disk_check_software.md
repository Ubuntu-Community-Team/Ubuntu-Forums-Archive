---
title: "long disk check software?"
date: 2009-09-15
forum: General Help
---

### Post by Arminius on 2009-09-15
I'm going away on holiday, and while I'm gone I'm wanting ubuntu to do a very long very comprehensive disk check, of every disk that's mounted, then when it's done it can just shut down the pc.

does such a thing exist?

---

### Post by scorp123 on 2009-09-15
> **Arminius said:**
> very comprehensive disk check, of every disk that's mounted That's a contradiction in itself. A disk that's mounted should not be checked. Ever. It's a good way to destroy whatever was on it.

And please: Let go of your Windows thinking. Ubuntu will check your disks when it thinks it needs to. Leave those settings alone if you don't understand them.

But to answer your question nontheless:

You could boot from a live CD and then trigger "fsck -f" against your harddisk partitions from there.

---

### Post by Arminius on 2009-09-15
was hoping to get ubunutu to do it, so it won't wanna do a disk check when I'm logging on and it's not convenient

---

### Post by con on 2009-11-02
I think this is what you want.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by Arminius on 2009-11-05
it's a nice start, I'm using it, just wish it wouldn't completely shut down when it finishes the scans.

---

