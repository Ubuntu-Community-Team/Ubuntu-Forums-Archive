---
title: "Synaptic Package Manager Error"
date: 2010-04-02
forum: General Help
---

### Post by mmosier1 on 2010-04-02
I get the following error when I try to launch Synaptic Package Manager in Linux 9.10. This started after my computer itself down during an attempted install of the Opera package downloaded from the Opera website.

E: Type '/dev/sda5' is not known on line 1 in source list /etc/apt/sources.list.d/opera.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any help in fixing this is much appreciated.

mm

---

### Post by kokkus on 2010-04-02
Open terminal and type in gksudo nautilus.
Now when you have root access to your files you can navigate to
/etc/apt/sources.list.d/opera.list and fix the bug by erasing the first line
/dev/sda5.

---

### Post by mmosier1 on 2010-04-04
Thanks!

---

