---
title: "Onboard graphics drivers not available, MSI motherboard-  K8M Neo-V"
date: 2010-04-18
forum: General Help
---

### Post by zegulas on 2010-04-18
Hello,
  I recently installed Ubuntu 9.10 after using Windows for more than 8 years. I just have one major problem, the webpage scrolling is not as smooth as it was in Windows, I guess because of the drivers. It looks very similar to how it looked in Windows without the graphic's driver installed.
  My motherboard is MSI K8M Neo-V. With on-board graphics.

---

### Post by clhsharky on 2010-04-18
Hi 

VIA doest support Linux very well. You probably all ready have the only driver for that old of VIA chip, all ready installed by default.

Sharky

---

### Post by 3rdalbum on 2010-04-18
You could enable "smooth scrolling" in Firefox, but IMHO it looks pretty awful, and it'll probably look even worse on a VIA graphics chip.

---

### Post by zegulas on 2010-04-18
So no other option except for upgrading my hardware? :(

---

### Post by lidex on 2010-04-18
Double check your graphics hardware with this command:
```
sudo lspci -nn | grep VGA
```
Then check this out:
[http://ubuntuforums.org/showthread.php?t=1340466]("http://ubuntuforums.org/showthread.php?t=1340466")
And/or do a search of the forums with vga controller name returned by the terminal.

---

### Post by zegulas on 2010-04-18
@lidex, this is what came up:
```
01:00.0 VGA compatible controller [0300]: VIA Technologies, 
Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] [1106:3108] (rev 01)

```

---

### Post by zegulas on 2010-04-21
@lidex, The post you referred didn't help.

---

### Post by chris3000 on 2010-04-24
Hello,

first, i am from germany and my english is very bad...

second, i am using gentoo but i use the same board (first as a main-board - now for a little server...) the sad answer for your problem is that problyable you have 3d-support like windows will never with the onboard graphic ship but a project has coded a driver that works good for common use (firefox and 2d acceleration works very good, wrote this from this motherboard :))

google for "openchrome" theren a some packages in ubuntu for this and you have to google for some parameters in the xorg.conf....

[http://www.openchrome.org/](http://www.openchrome.org/)
[http://wiki.ubuntuusers.de/Archiv/Grafikkarten/Via](http://wiki.ubuntuusers.de/Archiv/Grafikkarten/Via) (maybe to old...)
[http://wiki.ubuntuusers.de/Grafikkarten/Via-Grafikkarten/Unichrome9](http://wiki.ubuntuusers.de/Grafikkarten/Via-Grafikkarten/Unichrome9) (too...)
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) (for your language ;))

ihave googled for some new tricks for suspend to ram by this board and found your post :-)

i can rmind me where i buyed this board and wait for a 3d driver in linux... moths... years... and years.... and now... it is of a good way... after 8(?) years.... but for 3d unstable - only openarena is a little bit good playable... but for office user (or server) okay.

have luck!

ps: i dont know whether answer a second time... mayby... we will see...

greetings from german and sorry for my terrible english...

---

