---
title: "wallpaper-tray"
date: 2009-12-19
forum: General Help
---

### Post by cancer10 on 2009-12-19
Hi

I have successfully installed "wallpaper-tray" from the Synaptic Package manager but I do not see it anywhere under Applications.

Does anyone know where can I find it?


Thanks

---

### Post by sisco311 on 2009-12-19
wallpaper-tray is a GNOME Panel Applet. 

Right click on the panel -> Add to panel... -> Wallpaper Tray -> Add

---

### Post by cancer10 on 2009-12-19
I installed it succesfully but when I restart my comp I get the following error

> 
"Wallpaper Tray" has quit unexpectedly

If you reload a panel object, it will automatically be added back to the panel.

and the application crashes.

Any idea whats going on.


One thing I noticed though, one of the disk partition does not automatically load unless I go to "Computer" and double click on it, once i do so, i see the HDD icon on my desktop. 

1. Could this be the cause of the crashing of the wallpaper-tray?
2. How can I make ubuntu autoload that partition?

---

### Post by sisco311 on 2009-12-19
> **cancer10 said:**
> I installed it succesfully but when I restart my comp I get the following error



and the application crashes.

Any idea whats going on.


One thing I noticed though, one of the disk partition does not automatically load unless I go to "Computer" and double click on it, once i do so, i see the HDD icon on my desktop. 

1. Could this be the cause of the crashing of the wallpaper-tray?
2. How can I make ubuntu autoload that partition?

Are the wallpapers on that partitions?

What filesystem is on drive?

---

### Post by cancer10 on 2009-12-19
> **sisco311 said:**
> Are the wallpapers on that partitions?

What filesystem is on drive?

1. Yes, wallpapers are on that partition.

2. filesystem is ntfs-3g (3.1) (screenshot attached)

---

### Post by nishant.singh28 on 2009-12-19
> **cancer10 said:**
> 1. Yes, wallpapers are on that partition.

2. filesystem is ntfs-3g (3.1) (screenshot attached)
Get ntfs-config from Package Manager and enable write support for internal device in that drive...Bingo!!!!

---

### Post by cancer10 on 2009-12-19
> **nishant.singh28 said:**
> Get ntfs-config from Package Manager and enable write support for internal device in that drive...Bingo!!!!


I am done installing ntfs-config. Now how do I "enable write support for internal device"???


pls advise :)

---

### Post by sisco311 on 2009-12-19
> **cancer10 said:**
> I am done installing ntfs-config. Now how do I "enable write support for internal device"???


pls advise :)

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by cancer10 on 2009-12-20
> **sisco311 said:**
> [http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

Hey,

I followed the tutorial, but when I open the "NTFS Configuration Tool" it shows me the "Enable write support for internal device" as disabled (screeenshot attached).


Then I followed [this]("http://psychocats.net/ubuntu/mountwindowsfstab") tutorial.

I run the sudo fdisk -l command and it shows me a screen as attached screenshot.

and after doing the necessary changes, now my /etc/fstab  looks like the one as attached screenshot.


After doing all necessary changes and reboot my system, my ntfs partition disappeared. :(


So to get the ntfs partition back, i went ahead, edited the /etc/fstab file and commented the line which says

```
/dev/sda5 /windows ntfs-3g defaults,locale=en_IN 0 0
```


and after reboot my ntfs partition is back but my problem is still not resolved :(


Am I doing something wrong?

Pls help :)

Thanks

---

### Post by cancer10 on 2009-12-20
Any reply will be highly appreciated

---

