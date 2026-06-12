---
title: "Ubuntu splash screen issues"
date: 2010-12-29
forum: General Help
---

### Post by pljehyun on 2010-12-29
Hello, after installing a proprietary nvidia driver for 9800GTX+ on a fresh install, i started getting a simple text splash screen (purple with low-res "ubuntu" text).

i'm running a 1920x1080 desktop env, and i tried these tutorials
- [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
- [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

now i have a pretty high-res grub menu :p and the splash screen has the proper ubuntu loader (glowing ubuntu font), but there are large black borders around the splash and it also is not at full-res.

does anybody know how to fix this? if not is there a way to have a pure black startup instead of the splash? sorry if i explained it weird :confused:

---

### Post by dino99 on 2010-12-29
into a terminal, try:

sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth

note: for faster breakage(s), use untrusted url/howto. If you hate breakage, only follow ubuntu doc and ubuntu packages (see synaptic)

---

### Post by pljehyun on 2010-12-29
i get that jockey is not installed and the plymouth command does not affect the splash screen.

and the "untrusted url/howto" were recommended in the ubuntu forums so i thought I would try them..

---

