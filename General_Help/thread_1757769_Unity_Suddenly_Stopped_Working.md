---
title: "Unity Suddenly Stopped Working"
date: 2011-05-13
forum: General Help
---

### Post by plzdontkillme11 on 2011-05-13
Hey guys, I have no idea what happened. When I restarted my laptop a message telling me that my hardware cannot support Unity came up. This is quite impossible, because I've been running Unity with no problems since 11.04 was released.

Compiz says that the interface is unity, and when I checked in login screen, it's not set to Ubuntu Classic or anything, just Ubuntu.

Help would be appreciated. 

Thanks!

---

### Post by mc4man on 2011-05-13
Just to ck. what does this report
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by plzdontkillme11 on 2011-05-13
Hey, sorry for the late response. It returned "Segmentation fault."

---

### Post by NormanFLinux on 2011-05-13
Uh oh. Unity crashed. You may try reinstalling it but if the Unity crash reoccurs, switch to Unity 2D.

---

### Post by mc4man on 2011-05-13
> **plzdontkillme11 said:**
> Hey, sorry for the late response. It returned "Segmentation fault."

That seems to be a new one - I believe there was an update after release to unity/nux packages that blacklisted some cards. 
What card/driver are you using?
will show card
```
sudo lshw -C display
``` 

Maybe also log out and then into Classic or Classic(no effects) and try the unity_support command again

---

### Post by plzdontkillme11 on 2011-05-13
Alright, first my graphics card: 

```
sudo lshw -C display
[sudo] password for vignesh: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d35fffff


```

I will try reinstalling, and if that doesn't work, switch to Ubuntu Classic then reinstall. I'll tell you guys how it went.

---

### Post by plzdontkillme11 on 2011-05-13
Unity_support still returns Segmentation Error. Reinstalling Unity didn't do anything. :\

Am I better off using Gnome 3?

---

### Post by mc4man on 2011-05-13
Myself don't know about Intel cards - the update referred to was for certain nvidia cards so that wasn't it

(you could try booting to a live session (live cd or usb) and see if it works there

---

### Post by plzdontkillme11 on 2011-05-13
Hmm alright. But before I boot into a live cd, do you think there's anything else I can do?

Nevermind about Gnome 3, it seems too risky.

Thanks for the help!

---

### Post by NormanFLinux on 2011-05-13
Install Unity 2D. It should work.

---

### Post by plzdontkillme11 on 2011-05-13
Thanks very much, installing Unity 2d did the trick. :)

---

### Post by Mine's Ultimate R on 2011-06-15
Okay. So how do you explain why the original configuration suddenly stopped working? I also had this problem.

---

### Post by kenbo on 2011-07-01
I too now have this problem. I'm using an acer aspire one. Unity worked fine until I ran update manager yesterday. Also playing videos now crashes the player (tried vlc and smplayer)

Edit:Just ran another update. Xserver-common and Xorg.core updated and now all is well.

---

