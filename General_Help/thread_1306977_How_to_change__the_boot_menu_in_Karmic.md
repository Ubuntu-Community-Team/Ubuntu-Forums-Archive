---
title: "How to change  the boot menu in Karmic?"
date: 2009-10-30
forum: General Help
---

### Post by Strohfeuer on 2009-10-30
Does anybody know how I can change the Grub boot menu?
Like in this article:
[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

I did this before in Ubuntu 9.04 but now there is **no** menu.lst file in boot/grub.

---

### Post by arepaking on 2009-10-30
What!? I just realized the same thing bro!
I have another hard drive that runs Windows and I also need to change my GRUB options! but I don't find the way to do so.

Looks like we are in the same boat.

---

### Post by arepaking on 2009-10-30
Strohfeuer,
Take a look to this article. It might help

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen](http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen)

Looks like menu.lst It has been replaced by ''/boot/grub/grub.cfg''. But The main menu file, ''/boot/grub/grub.cfg'' is not meant to be edited, even by 'root'.

---

### Post by Strohfeuer on 2009-10-30
> **arepaking said:**
> Strohfeuer,
Take a look to this article. It might help

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen](http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen)

Looks like menu.lst It has been replaced by ''/boot/grub/grub.cfg''. But The main menu file, ''/boot/grub/grub.cfg'' is not meant to be edited, even by 'root'.

Thanks a lot bro! Seems we have to create a custom file. I would rather not be the first how will try it. Any volunteers? ;)

---

### Post by arepaking on 2009-10-30
I'm stuck here since I don't now how to make my other HD to boot on windows... :(

I tried to copy and paste the string that I had for the menu.lst into the /etc/grub.d/40_custom but it did not work at all.. it booted directly into Ubuntu

---

### Post by Strohfeuer on 2009-10-30
> **arepaking said:**
> I'm stuck here since I don't now how to make my other HD to boot on windows... :(

I tried to copy and paste the string that I had for the menu.lst into the /etc/grub.d/40_custom but it did not work at all.. it booted directly into Ubuntu

I'm sorry that I can't help you here. I have Windows and Ubuntu on the same hard drive. Dual booting works fine here, but I would like to hide the boot menu. It's late here so I will do further research tomorrow.

---

