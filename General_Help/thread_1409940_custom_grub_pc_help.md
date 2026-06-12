---
title: "custom grub pc help"
date: 2010-02-18
forum: General Help
---

### Post by cwalker1960 on 2010-02-18
I created a custom file in etc/grub.d/   using the lines from grub.cfg  . I have win xp installed on sda1 and sdb1. the os prober found both and boot fine ,,now in my custom file  there is a line  drivemap -s(hdo) ${root}    when i run grub update , the ${root} is left out. of the line. on my custom menu.. I have added it manually to grub cfg and all works fine ,but  ,, how do I make grub write it as should in my custom file?

---

### Post by cwalker1960 on 2010-02-18
solved  i had to put a \ in front of the $ sign in my custom menu,,

---

