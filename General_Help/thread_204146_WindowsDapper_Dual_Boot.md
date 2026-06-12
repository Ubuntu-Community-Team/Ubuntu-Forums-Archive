---
title: "Windows/Dapper Dual Boot"
date: 2006-06-26
forum: General Help
---

### Post by djbjrca on 2006-06-26
I recently for work-related purposes obtained a copy of WIndows XP Home Edition.  The disc works fine on each of the three computers we installed it on.

I have a 6.06 running on my home computer right now, and I LOVE it, but I was thinking of installing Windows to dual boot (in order to play Myst 4, which I have only completed half of).

I know you are supposed to install Linux last and all that, but I have a lot of good stuff on my install right now that I dont want to loose so I was wondering if anyone had tried this and if not if anyone knows whether or not it is possible to do.  Thanks.

---

### Post by angkor on 2006-06-26
It is possible, you just need to reinstall grub after you've installed windows to be able to log into your ubtunu again. Search the forum for reinstalling grub for a howto (it's done with the liveCD/ DesktopCD).

Backup your important data nonetheless.

Edit: Did a search for you :)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tomski on 2006-06-26
when you have installed all you like in windows insert the dapper cd & reboot
at the boot promt type:
rescue

then give the root password 
& then type:
grub-install /dev/hd0

then reboot the sytem
it should find it, if not then add this to /boot/grub/menu.lst

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Menu
root		(hd0,0)
savedefault
makeactive
chainloader	+1

then type:
grub-install /dev/hd0 

and reboot


i hope this helps

---

### Post by djbjrca on 2006-06-26
Thank you both, I will try it and post results.

---

### Post by djbjrca on 2006-06-27
Alright sorry for the double post.

It worked.  I am writing this in Windows right now, having just left Linux.

I sort of mixed and matched the two replies and had to do a little bit on my own (mostly just partition numbers and stuff like that) but in the end it worked.

Thanks a lot.

---

