---
title: "changing grub boot order"
date: 2010-03-05
forum: General Help
---

### Post by dodderer on 2010-03-05
I run Win 2000 and Ubuntu 8.04 on an Acer Veriton after some fiddling I lost windows from the boot list. After several unsuccessful attemts at editing the grub menu list and using startup manager Idid the following :: 1. in Sum entered Windows as the default starter
2.changed time out And Then

Code:

sudo apt-get update

Then after that finished,  'sudo apt-get upgrade'.
Code:

sudo apt-get upgrade

then re-installing GRUB to MBR with 'sudo grub-install /dev/sda'.
Code:

sudo grub-install /dev/sda

I do not know exactly what happened but I got the result I was after .Seems to me sum cant manage on its own.

---

