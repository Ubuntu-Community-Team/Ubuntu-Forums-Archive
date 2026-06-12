---
title: "GNU GRUB version 1.97~beta4 issues no dual boot"
date: 2010-01-15
forum: General Help
---

### Post by bublehead688 on 2010-01-15
I have been using Karmic for a month or two now and the recent release of the GRUB loader 1.97~beta4 isn't loading. My machine loads to a console screen and allows me to select a different loader (the previous one) that works. The following does not load in generic or safe mode. "Ubuntu Linux 2.6.31-17-generic"  I end up selecting the "-16-generic" and that works for me. 
The reason I choose to post separately is because I am not using a dual boot system like most of the other threads are using. I only run Karmic on my laptop. Laptop is an Acer Aspire 5315.
Major admiration goes to the first person who can help me!

---

### Post by Leppie on 2010-01-15
i'm not quite sure i fully understand the issue.
you have grub2 and grub legacy installed and only grub legacy is working properly? furthermore the most recent kernel (17) cannot be booted?

i think the grub issue can be solve with these commands:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```
this will completely remove all instances of grub on your system and then install grub2 (setup screens will follow the installation).

---

