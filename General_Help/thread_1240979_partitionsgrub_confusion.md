---
title: "partitions/grub confusion"
date: 2009-08-15
forum: General Help
---

### Post by gumblina on 2009-08-15
Hi,

I hope someone can help me. I've got a dual boot of xp and ubuntu 9.04 (UNR) on my samsung nc10. I've been using ubuntu for a few months and I really like it (except that videos and webgames don't work properly - I'm going to try the workaround soon to try and fix it). The only thing is, I think I might have done something wrong when first installing it, as my partitions look messy and I'm totally confused about how to fix it! I don't want to start deleting them, in case I break something.
Also, for some reason, I've got another entry for ubuntu on my grub menu. I already had two, I don't know why, and now there's three!
The grub menu now looks like this:
ubuntu 9.04 kernel 2.6.28.14 generic
ubuntu 9.04 kernel 2.6.28.14 generic recovery 
ubuntu 9.04 kernel 2.6.28.13 generic
ubuntu 9.04 kernel 2.6.28.13 generic recovery
ubuntu 9.04 kernel 2.6.28.11 generic
ubuntu 9.04 kernel 2.6.28.11 generic recovery
ubuntu 9.04 memtest +86
other
windows vista (loader)
windows xp

all three of the ubuntu choices are the same, and all boot from hd0,5 ext3.

Can anyone help me sort this out? I've tried reading up about it, and I think I'm more confused than I was before! I've attached a screenshot of the partitions, in case that will shed any light on it.

Thanks :)

---

### Post by Bachstelze on 2009-08-15
Nothing wrong with your partitions. If your GRUB has all those entries, it's because a new one is added every time a new kernel is installed for your Ubuntu, in order to let you boot the old one should the new one fail somehow. If the new one works fine, you can uninstall the old one, which will remove the GRUB entry. Look for packages named [font=monospace]linux-image[/font] (but it's generally a good idea to leave at least two).

---

### Post by gumblina on 2009-08-15
thanks for the quick reply! I'm glad there's nothing wrong then, I def need to learn more about this so I understand what's going on properly :)

---

### Post by AlexanderDGreat on 2009-08-15
Hi, I think nothing's wrong with your partitions, in Linux, sda is the common harddisk, when you add a partition it goes: sda1, sda2, sda5, sda6, etc...

It jumps to sda5 because there can only be 4 primary partitions (up to sda4) in our harddisks so sda5 is an extended partition, in case you chose logical.

Try typing this: nano /boot/grub/menu.lst

Look under "default" and that's your automatic OS on startup, if you type default 4, it means you have to count 0 - 4, these are the titles/OS'es in your boot loader, they're located if you scroll down a bit more, your OS'es always start with Title: Kernel, Title: Windows XP, Title: Windows Vista, Title, etc...

Did you just run apt-get update, apt-get upgrade on your system? If you did, it automatically installs new kernel versions so that's why you have lots of kernels, but you can always modify these in your /boot/grub/menu.lst

Hope to help.

---

### Post by gumblina on 2009-08-15
thanks :) i didn't know that, it makes a bit more sense now :KS

i think i'll leave them all on there, now i know that its ok and i haven't mysteriously ballsed up my comp!

---

