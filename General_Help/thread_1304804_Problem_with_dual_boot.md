---
title: "Problem with dual boot"
date: 2009-10-29
forum: General Help
---

### Post by lithmariel on 2009-10-29
Windows got screwed because somene messed with power, I tried to install again, but after like 5 mminutes of instalation passes, it stops on a black screen. But this is not the main problem, as this one seems to just be my windows CD. The thing is that I dont have option while booting to go for ubuntu anymore, theres just windows on the list (I checked which partition it was before installing, so Im sure it was the right one) 

Any solutions to fix that problem or I deceived to use the kurumin live CD much longer xD

---

### Post by dvlchd3 on 2009-10-29
When you reinstall Windows it takes over your MBR.

See link for recovering GRUB:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lithmariel on 2009-10-29
Seems simple. Time to go steal my brothers ubuntu CD.

Thanks.

---

### Post by lithmariel on 2009-10-31
Um..... So I did everything there and went to the last part, but I get this

root@ubuntu:~# sudo grub-install --root-directory=/media/root /dev/sda2
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator


And it seems to never finish that process. Trying the other command that could be used if you got errors end with same thing.

---

