---
title: "grub-reboot problems"
date: 2010-03-12
forum: General Help
---

### Post by Edwinem on 2010-03-12
So while trying to figure out how to set it up that my computer would restart automatically into windows I came across the **grub-reboot** command. However whenever I use it, does not seem to do anything. I have run it as sudo and used both the number and the menuentry, yet nothing happened. While trying to figure this out a lot of sites said to change something in the menu.lst. However, I am running grub 2.0 and the menu.lst does not exist any more. I am wondering if I have to change something in the grub.cfg file, but I do not trust myself enough to play around with it.

P.S If anybody knows a better way to set it up that your computer reboots from Ubuntu to windows please tell me.

---

### Post by sebth on 2010-03-20
Did you set GRUB_DEFAULT=saved in /etc/default/grub ? (Don't forget to run update-grub after modifying the config file)

I found a nice post about grub2 : [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by oldfred on 2010-03-20
This will set the default to boot from a windows stanza:

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved
Then do sudo update-grub.

---

