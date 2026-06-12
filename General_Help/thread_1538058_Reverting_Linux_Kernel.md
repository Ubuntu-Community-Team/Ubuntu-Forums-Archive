---
title: "Reverting Linux Kernel"
date: 2010-07-24
forum: General Help
---

### Post by Bonechilla on 2010-07-24
I am using Ubuntu Studio and today ran an update originally their was nothing found but when i clicked check it found a kernel to update; however after installing the new kernel I've been having problems the system constantly freezes a lot of my processes do not work properly and if i log out it freezes at a black screen. I was attempting to revert to the older kernel however I realized that [COLOR="Red"]i do not have grub[/COLOR] (at least that is what i am guessing since /boot/grub/menu.lst is missing an actually their are a lot of audio files in that folder) installed is their any other way to revert to an older kernel

---

### Post by howefield on 2010-07-24
> **Bonechilla said:**
> I was attempting to revert to the older kernel

Pressing the shift key quickly after the BIOS boots should bring up the grub menu, you have to be quick, there isn't a large window between the BIOS booting and the Ubuntu splash screen.

For information on Grub2, which by the sound of it you are running...

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by cchhrriiss121212 on 2010-07-24
Try using startup manager to see what kernels you have installed and change the default one if necessary.

---

### Post by howefield on 2010-07-24
> **cchhrriiss121212 said:**
> Try using startup manager to see what kernels you have installed and change the default one if necessary.

Just to add to the comment re startupmanager..

> StartUp-Manager supports Grub 2, but not all options are available. The two most-used items, however, are: setting the default kernel/OS and setting the menu timeout delay. There are plans for a StartUp-Manager 2 that works only for Grub 2 but it is still under development according to its creator. To view a guide on installing and running StartUpManager, view the StartUpManager community doc or the forum post on which it was based: [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Bonechilla on 2010-07-25
thanks for the replies and explanation i realized that it was grub2 that i had i opened cfg to edit it and it seemed very different so i installed startup manager and found I had 3 kernels installed so i reverted to the previous one...

Thanks for the help

---

