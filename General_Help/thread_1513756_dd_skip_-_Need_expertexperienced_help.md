---
title: "dd skip - Need expert/experienced help"
date: 2010-06-20
forum: General Help
---

### Post by ic2 on 2010-06-20
I working with two identical sized 10GB partitions.  10,742,183,424 BYTES each.

**I read:**

> dd
Convert and copy a file. Copy standard input to the standard output. Input data is read and written in 512-byte blocks.
 
[http://ss64.com/osx/dd.html](http://ss64.com/osx/dd.html)

**So I divide:**
[COLOR="Red"]10742183424 / 512 =  20980827 BLOCKS[/COLOR]

This is how I plan to copy both partitions to a 32GB USB Flash Drive.

```
dd if=/dev/sda1 of=/dev/sdb1 bs=1M

dd if=/dev/sda2 of=/dev/sdb1 skip=20980827 bs=1M
```

Is the skip size in BLOCKS correct?
Is the entire code correct to do what I am after?

---

