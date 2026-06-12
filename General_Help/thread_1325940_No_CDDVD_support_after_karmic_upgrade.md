---
title: "No CD/DVD support after karmic upgrade"
date: 2009-11-13
forum: General Help
---

### Post by rcorbish on 2009-11-13
Upgraded to karmic from jaunty 

Now There's no CD available.

lshw shows no cdrom
[FONT="Courier New"]sudo lshw | grep cdrom
[/FONT]
has no output

fstab has the definition 
[FONT="Courier New"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/FONT]

Are there any known issues - this CD did use to work at one time. I don't use it much but when I needed it it's gone!

Thanks for any insight

RC

---

