---
title: "3com ethernet card"
date: 2010-05-24
forum: General Help
---

### Post by wayland on 2010-05-24
I have an old computer that I was thinking to use as a server. I have experience with terminal and apache under mac os x , but not enough that I would be completely comfortable without a gui, so I installed the standard 9.10 desktop build.

Ubuntu doesn't seem to be recognizing the ethernet card, though. Google says to type lspci -nn in the terminal, and among other (I'm thinking mostly irrelevant) things it returns:

```

01:0c.0 Ethernet controller [0200]: 3com Corporation 3c905c-TX/TX-M [Tornado] [10b7:9200] (rev 78)

```

What do I do? I have virtually no experience compiling drivers or really with linux at all, but I'm willing to get my feet wet with a little hand-holding.

---

### Post by whoop on 2010-05-24
Could be just an ubuntu issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356148](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356148)

It has been reported working fine under other distros...

---

### Post by wayland on 2010-05-24
I have tried the same computer under Fedora 12 with the same results.

Is there anything I can do other than installing something else? Any recommendations on what something else I should install?

---

