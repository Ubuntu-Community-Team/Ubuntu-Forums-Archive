---
title: "Grub + Partition Help"
date: 2006-03-31
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-03-31
Hi, I recently resized my default Ubuntu partition and created a spare partition that I installed dapper on. When I start my computer, grub auto highlights dapper. How can I...

1. Remove my dapper partition and but it back onto my main ubuntu partition.

2. Reorder my bootlist and make ubuntu first.

I just installed dapper to see what it was like and it is progressing very nicely. I can't wait for it :) I don't have a problem with removing it, breezy is fine for now.

---

### Post by Ramses de Norre on 2006-03-31
To remove dapper: just remove the files on the partition, you can use it for breezy again then.

Grub: sudo gedit /boot/grub/menu.lst  delete the dapper block (assuming you removed dapper).

---

