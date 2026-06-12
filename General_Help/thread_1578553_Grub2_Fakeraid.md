---
title: "Grub2 Fakeraid"
date: 2010-09-20
forum: General Help
---

### Post by h4ck3r on 2010-09-20
A question about grub 2. I recently installed ubuntu 10.04 on a fakeraid (ich10r) and have it working. I used grub though to get it working. I since then have installed grub 2, but haven't written it to the mbr. My question is will it work properly? It won't run immediately when I chainload into it from Grub, but if I set root from (hd0,0) to (hd0,2) which is where my linux is, it'll start just fine. when I do upgrade-from-grub-legacy will this be a problem? or is there a way to change it so that when I do run upgrade-from-grub-legacy it'll be set to "root (hd0,2)"?

---

