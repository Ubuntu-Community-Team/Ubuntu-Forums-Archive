---
title: "Graphics problems after upgrade from 10.04"
date: 2010-10-21
forum: General Help
---

### Post by Infil on 2010-10-21
I have a Radeon HD4570 Mobility in my laptop. I upgraded from 10.04 64-bit to 10.10 64-bit. In Ubuntu 10.04 desktop effects were working pitch-perfect with the default radeon-driver. After I upgraded to 10.10, I cannot choose normal or extra desktop effects at all. I also don't get native resolution on my external monitor in the terminal which I did in 10.04.

During boot I get an error regarding "dynpm" being unknown. A couple of months back I added "radeon.dynpm=1" to the kernel line. But now even if that isn't there in 10_linux in /etc/grub.d/ it is still there in /boot/grub.cfg after it is auto-generated. 

I think maybe these problems are related. Someone said removing the Compiz PPA fixed the desktop effects issue, but I have never used the Compiz PPA.

I will try to do a separate clean install of 10.10 later today. I did fool around quite a bit with xorg-edgers and kernels from the PPA and what-not this spring. Maybe there are some "leftovers".

---

### Post by Infil on 2010-10-21
I have desktop effects even in the live CD environment, so perhaps its best to do a clean install.

---

