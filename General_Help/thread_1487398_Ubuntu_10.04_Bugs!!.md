---
title: "Ubuntu 10.04 Bugs!!"
date: 2010-05-18
forum: General Help
---

### Post by Tylerjay on 2010-05-18
I am getting random blips of the screen. the longest one was almost a second.
every 10 min or so, the whole screen will blip/flash lines across. It does not effect the proformance as far as I can tell. but maybe all you people out there know better. Is there something i can do  about this or does it not even matter?

---

### Post by pytheas22 on 2010-05-19
That's strange.  If you have any other operating systems installed on this same computer, do you experience the blips there as well?  Or if you pause the system during the boot process before Ubuntu starts loading (on most computers you can enter setup by pressing a key like F2 or escape shortly after powering the machine on; look at the startup screen for specific instructions), does it still blip?  If so, it's probably a hardware issue, unfortunately.

If the problem only happens in Ubuntu, it could be a problem with your video driver.  In that case, if you post the output of the following commands, it should hopefully help figure out how to fix it:
```

cat /etc/issue
uname -a
lspci -nn | grep -i vga
lshw -C display
```

---

