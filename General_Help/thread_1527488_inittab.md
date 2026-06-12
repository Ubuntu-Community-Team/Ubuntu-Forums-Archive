---
title: "inittab"
date: 2010-07-09
forum: General Help
---

### Post by jithin_tk on 2010-07-09
I installed ubuntu 10.04 LTS.. but I couldnt see the file /etc/inittab,, so I couldn't set command mode as default. Will you help me???

---

### Post by Tipo on 2010-07-09
What do you mean by "command mode"? A runlevel without X11?

Ubuntu doesn't use /etc/inittab by default (source: man inittab). You can see information about setting the default runlevel by looking at /etc/init/rc-sysinit.conf. The comments in that file are helpful :smile:

---

### Post by Estee67 on 2010-07-30
Also /usr/share/doc/upstart/README.Debian.gz might be of interest. :-)

---

### Post by sisco311 on 2010-07-30
> **jithin_tk said:**
> I installed ubuntu 10.04 LTS.. but I couldnt see the file /etc/inittab,, so I couldn't set command mode as default. Will you help me???

[post=9644518]Check this out. =)[/post]

---

