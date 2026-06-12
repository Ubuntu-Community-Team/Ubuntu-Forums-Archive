---
title: "GRUB problem - 11.10"
date: 2011-10-29
forum: General Help
---

### Post by biuro74 on 2011-10-29
Hi,

I'm tired :) All the time I upgrade Ubuntu, new issue arises.
This time (11.04 - 11.10) I've experienced strange GRUB behaviour. My system is multiboot, with GRUB2 as starter for everything. After upgrade, Ubuntu.. disappeared from bootmenu list. I've got customized GRUB, as described here:

[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

and - simply - my /etc/grub.d/10_linux and 30_os-prober were chmodded with -x as I've got custom bootlist.
When I do chmod +x to 10_linux - Ubuntu appears, but with other options (like 2 kernels and something else). I try to keep my menulist clean and tidy, so any help appreciated.

BTW, my bootpicture has changed, too... and I have no idea how to get it back. I underline the way mentioned above (in link) doesn't work. And yes, I do "sudo update-grub" after any change :)

Thanks in advance

---

