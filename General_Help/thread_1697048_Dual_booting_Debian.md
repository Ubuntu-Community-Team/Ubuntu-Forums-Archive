---
title: "Dual booting Debian"
date: 2011-02-28
forum: General Help
---

### Post by humturtle39 on 2011-02-28
I fancy giving Debian a whirl, seeing as it's one of the few distros I've not tried, and was just wondering if dual-booting Debian and Ubuntu was reasonably easy to do, like, if I use Gparted from a gnome live CD to create emtpy space, and then manually partition the space like I would for Ubuntu, ie. 8gb swap, 20GB root, the rest for home, would that work out?

Cheers

---

### Post by humturtle39 on 2011-02-28
I meant to add, sorry for this not really being an Ubuntu issue, I didn't want to go through the hassle of registering with the Debian forums and later find out I don't like it.

---

### Post by seawolf167 on 2011-02-28
Yup, pretty much that easy.

Create some free space with GParted, use the same swap partition and start the install. As usual, backup before you start in case something goes wrong. I like [Clonezilla]("http://www.clonezilla.org")

Note that 8GB swap is too much for a modern computer with 4GB or more of RAM. You could easily get away with 2GB of swap

---

### Post by humturtle39 on 2011-02-28
Yeah I've got 4GB RAM and ulways went for an 8GB swap 'cause I've read 'swap double the RAM' in a few places, but I must have reasonably light demands of my computer because in System Monitor I've never even seen swap used at all, never mind reach anything close to 8GB.

Last time I installed Ubuntu I just let the installer automatically format the drive and it gave me an 11GB swap, oh well

Thanks very much :D

---

