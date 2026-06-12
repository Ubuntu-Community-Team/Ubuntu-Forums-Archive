---
title: "Maverick USB boot - fstab always overwritten"
date: 2011-03-21
forum: General Help
---

### Post by rabinnh on 2011-03-21
I need to modify the fstab on my USB key installation, but every time I reboot it is overwritten.

I modify it and even make a copy (cp /etc/fstab /etc/fstab.new).  Persistence is working properly because the copy remains, but fstab itself is overwritten on every boot based on the date.

My guess is that this is some sort of automatic behaviour for this type of installation, but I cannot find any documentation anywhere of one of the following fixes:

1) Where this behaviour can be modified
2) Where the defaults are stored
3) Which init script is performing this unwanted and perfidious activity.

Any help would be appreciated.

---

