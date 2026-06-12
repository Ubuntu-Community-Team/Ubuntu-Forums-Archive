---
title: "autofs loopback mounts"
date: 2010-05-02
forum: General Help
---

### Post by slvr42 on 2010-05-02
What I'm trying to accomplish is to mount a folder called /export/Downloads in every users home directory as Downloads.

I would have thought that an auto direct would work but for the life of me I can't figure out what's going on.

My auto.master file reads
/- /etc/auto.direct

auto.direct reads
$HOME/Downloads -fstype=auto,rw :/export/Downloads

Do auto directs just not work in Linux or what?

Also I'm not getting any errors in syslog or messages when I start autofs.

---

### Post by foobar66 on 2010-05-18
First - I am not 100% sure - but I do not think that the reference to $HOME will properly work. I believe the autofs conf files are read at daemon startup.

How did you start the autofs ?
Did you have proper kernel/module support enabled for automounting?

---

