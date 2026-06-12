---
title: "BURG with only one OS?"
date: 2010-07-14
forum: General Help
---

### Post by Cloudkookoo on 2010-07-14
So I'm hearing alot about this BURG lately and I'm running only one OS on this PC (Ubuntu Lynx) so I wanna know if BURG would be a good idea to install just to make the boot screen a bit more spiffy.

---

### Post by davidmohammed on 2010-07-14
seems pointless to me - how long is your wait between your bios screen message and the standard ubuntu splash screen?

---

### Post by Cloudkookoo on 2010-07-14
Not very long, my system is pretty clean. I just like making things look more appealing when there is room for improvement :p

---

### Post by davidmohammed on 2010-07-14
suggest look at the file

/etc/default/grub

make sure GRUB_DEFAULT=0 and GRUB_TIMEOUT=0

run

sudo update-grub

this should reduce the time between your bios and the ubuntu splash to hopefully less than 1 second...

---

