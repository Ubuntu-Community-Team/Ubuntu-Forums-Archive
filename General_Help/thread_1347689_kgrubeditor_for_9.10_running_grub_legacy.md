---
title: "kgrubeditor for 9.10 running grub legacy"
date: 2009-12-06
forum: General Help
---

### Post by pieguy on 2009-12-06
I need a grub editor like kgrubeditor for 9.10 x64 running grub legacy.  I cant find kgrubeditor in spm so I need an alternative.  I'm unaware/unfamiliar with any others so I need suggests.

---

### Post by kennethadammiller on 2009-12-14
I need something to edit my grub as well. Someone please find us something. I can't find anything that will edit grub in 9.10

but hey for you up there, you can run sudo update-grub and that will find and update grub 2

if you have any external devices with any kind of previous grub installation it will add that to your grub, i like to have each media with multiple installations to have grub menus that are independent of each other. it just makes sense to me that way. 

anyway, if you want to edit it, i'll give you an example of what i did to remove previous references. I had two different references booting up, like one was 2.6.31-16, the other 2.6.31-14. I found and placed all references of the older one in /boot/2.6.31-14 and then ran sudo update-grub. That seemed to work.

you can see what the menu will say by going to /boot/grub/grub.cfg and /etc/default/grub   those two files will let you edit some of grub, but don't edit the one that's in /boot/grub. only reload it with the sudo update-grub command.

[http://cquirke.wordpress.com/2009/11/20/edit-grub-menu-in-ubuntu-9-10-and-older/](http://cquirke.wordpress.com/2009/11/20/edit-grub-menu-in-ubuntu-9-10-and-older/)

---

