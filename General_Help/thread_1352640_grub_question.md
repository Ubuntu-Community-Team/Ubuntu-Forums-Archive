---
title: "grub question"
date: 2009-12-11
forum: General Help
---

### Post by Ilovepenguins on 2009-12-11
Hi,
I had Ubuntu on my computer for a while exclusively, but then i decided to try out some more distros. I installed gOS and it made it's own grub, which was ok since I was able to simply add the Ubuntu entry and boot from that. Now I want to get rid of gOS, but  I don't know what will happen if I reformat it's partition. Will I still be able to boot into Ubuntu or will I have to reinstall GRUB somehow?
Thanks for your help!

---

### Post by bumanie on 2009-12-11
If gOS took over the control of grub you will have to format/delete the partition it is on and then reinstall grub. Assuming you are still using grub-legacy 0n 9.04 (as per you signature) follow [this]("http://hplipopensource.com/hplip-web/install_wizard/index.html"). If you have upgraded to grub2 - look [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD").

---

### Post by Ilovepenguins on 2009-12-11
Ok cool, I am using legacy grub, but the first link you posted seems to go to a HP printer drivers page.

---

### Post by bumanie on 2009-12-11
Oh, don't know what happened there - [look here]("http://ubuntuforums.org/showthread.php?t=224351") - and sorry.

---

### Post by Ilovepenguins on 2009-12-12
Cheers, works great.

---

