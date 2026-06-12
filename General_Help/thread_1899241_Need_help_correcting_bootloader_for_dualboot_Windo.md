---
title: "Need help correcting bootloader for dualboot Windows XP and Ubuntu 11.10"
date: 2011-12-23
forum: General Help
---

### Post by cdm2006 on 2011-12-23
I wanted to run OnLive on my netbook and the only way I could do that was to install Windows XP via WinToFlash via SDCard. I created a 15gb partition using parted magic and installed it successfully but now when I start up I get two options. 

Windows XP
(Default) Windows

No option to load Ubuntu. The Windows XP option says I can't load because I have a corrupt HAL.dll file or something of the sort, which is because of the WinToFlash program I used to install XP... but thats not a huge deal because the Default Windows option loads XP just fine. What I'd like to have is a simple load menu with XP as one option and Ubuntu as the other. I found this tutorial online that uses Grub via an Ubuntu 11.10 live disk:

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

Is this a good work around or is there different method I should use? Keep in mind I'm a novice at Linux. Also I fear there may be complications from where I used WinToFlash to install XP, if Grub points to the first option "Windows XP" and not "(Default) Windows" then I just might screw things up again.

All I wanted to do was play OnLive =[

Thanks guys.

---

### Post by sikander3786 on 2011-12-23
Nopes, the one you linked is probably not for you. However it should work but there is an even easier method of achieving the dual boot between Ubuntu and Windows 7.

You need to boot an Ubuntu Live CD/USB and simply run 3 commands, thats it:

Official page:
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

Same method but probably easier to understand:
[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

If you need the exact commands, please boot an Ubuntu Live CD/USB and post the output of following command. We'll give you 2 commands to be run from the same Live CD/USB and hopefully you'll be able to dualboot:

```
sudo fdisk -l
```

---

### Post by cdm2006 on 2011-12-23
> **sikander3786 said:**
> Nopes, the one you linked is probably not for you. However it should work but there is an even easier method of achieving the dual boot between Ubuntu and Windows 7.

You need to boot an Ubuntu Live CD/USB and simply run 3 commands, thats it:

Official page:
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

Same method but probably easier to understand:
[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

If you need the exact commands, please boot an Ubuntu Live CD/USB and post the output of following command. We'll give you 2 commands to be run from the same Live CD/USB and hopefully you'll be able to dualboot:

```
sudo fdisk -l
```

Thanks friend, I'll give this a try tomorrow as its five thirty in the morning here and I'll have to make my Live SDCard before I continue. I'll report back ASAP.

---

