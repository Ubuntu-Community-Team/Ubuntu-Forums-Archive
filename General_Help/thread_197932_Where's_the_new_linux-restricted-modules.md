---
title: "Where's the new linux-restricted-modules?"
date: 2006-06-16
forum: General Help
---

### Post by NeoChaosX on 2006-06-16
Okay, like some other folks have noted, there was a new kernel update (2.6.15-25) yesterday. However, I have yet to see a linux-restricted-modules update to go with this new kernel. For me this is really important, as I have an Atheros wireless card and I need the l-r-m package to get it to work. Anybody know if the new l-r-m package will be on it's way?

---

### Post by givré on 2006-06-16
It's depend of your local mirror, but i think it should be ok soon.
If you want it now, take it there
[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/)

---

### Post by Jucato on 2006-06-16
The new linux-restricted-modules are found in the dapper-security repositories, but you need to add/enable the restricted component for that, since it's not included by default (weird, really). I found that out the hard way... :(

---

### Post by NeoChaosX on 2006-06-16
Go fig; it's in a repo I don't have enabled. Thanks Fenyx.

---

