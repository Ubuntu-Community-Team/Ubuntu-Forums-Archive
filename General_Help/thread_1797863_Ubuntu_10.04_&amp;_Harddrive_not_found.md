---
title: "Ubuntu 10.04 &amp; Harddrive not found"
date: 2011-07-05
forum: General Help
---

### Post by oaxacamatt1 on 2011-07-05
Hi All,
I am running Ubuntu 10.04 and recently installed Linux Mint on an other partition.  I am now finding that when I boot up I get a message that Grub is unable to find a hard-dirve that does not exist.

Can someone remind me where I can info on how to tell Grub (or is it something/where else) not to look for a non-existent hard drive?  I am not a newb but don't deal with these things often.
Cheers,
M

---

### Post by seawolf167 on 2011-07-05
You should be able to simply boot into Ubuntu and run

```
sudo update-grub
```

If you don't have it already, you may need to install

```
sudo apt-get install os-prober
```

---

