---
title: "W: Couldn't stat source package..."
date: 2006-04-11
forum: General Help
---

### Post by foobar on 2006-04-11
every time i run 'apt-get' i always get these warnings at the end of the output.
```
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```
what shall i do to fix this?

---

### Post by localzuk on 2006-04-11
I would take a look in your /etc/apt/sources.list file (run sudo gedit /etc/apt/sources.list in a terminal window). Take a look at the line with the above mentioned url in it and replace it with theses 2:

```

deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

The mirrormax ones have been moved. Also, you may wish to update to breezy now as it is the current stable release.

---

### Post by foobar on 2006-04-11
thank you localzuk, that solved it.
as for updating to breezy, i had in the past (twice) and it was pure hell... i will wait for drake.

---

