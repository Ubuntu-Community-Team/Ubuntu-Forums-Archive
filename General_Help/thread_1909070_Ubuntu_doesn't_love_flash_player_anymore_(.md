---
title: "Ubuntu doesn't love flash player anymore :("
date: 2012-01-14
forum: General Help
---

### Post by EpicWorld on 2012-01-14
Due to an virus i had to nuke windows and reinstall it. I installed ubuntu on a different partition [local disk e]. I thought it won't affect my ubuntu if i nuke partion C and reinstall my windows, but it affected it, since whenever i start my laptop it automatically opens windows, without asking me what OS i want. I checked out partition E on windows and the wubi folders were empty. I tried to unistall wubi, but it didn't worked so i just permanently nuked the files and folders. After I reinstalled Ubuntu nothing was the same. I got an error when i tried to install flash player & plugin. Also got errors with Wine, Tux paint, etc. It says that it could not open packages. I tried a few times, but mostly i got errors and/or Ubuntu software center, Firefox, etc stopped working at the same time. So yeah, any help please?:confused:

Edit: Oh yeah the Windows I installed isn't like the old one. My cousin gave me a special windows for my laptop [acer aspire 5732Z] and it's how to say....ummm kinda weird, the screen resolution isn't good and i can only choose 800x600 or 1024x768 resolution, nothing else. And yeah it's not as good as the old one, can it affect Ubuntu?

---

### Post by krytorii on 2012-01-14
Did you install ubuntu in  a new partition or through wubi?

If you're on wubi, my advice would be to either uninstall wubi completely, delete any wubi folders left, then reinstall. Or, and this is much preferable, install ubuntu on it's own partition. Use these [instructions]("https://help.ubuntu.com/community/WindowsDualBoot")

Also, windows tends to take over the whole hard drive when you install it. I've managed to get xp to install on a particular partition, but I had to go out of my way to select that option. Chances are you're going to have to just reinstall ubuntu.

---

### Post by EpicWorld on 2012-01-14
> **krytorii said:**
> Did you install ubuntu in  a new partition or through wubi?

If you're on wubi, my advice would be to either uninstall wubi completely, delete any wubi folders left, then reinstall. Or, and this is much preferable, install ubuntu on it's own partition. Use these [instructions]("https://help.ubuntu.com/community/WindowsDualBoot")

Also, windows tends to take over the whole hard drive when you install it. I've managed to get xp to install on a particular partition, but I had to go out of my way to select that option. Chances are you're going to have to just reinstall ubuntu.

Windows is on partition C, while WUBI is on Partition E. On E i do have some files, i will try to install it on parition D, since is almost empty.

---

### Post by krytorii on 2012-01-14
Wubi is installed inside of windows. If you formatted your windows partition, you've most likely lost your wubi installation, the same as you would have lost any other program installed.

---

### Post by holycow131415 on 2012-01-14
Yea when you install ubuntu, chose the side by side install so that it isnt a wubi install

---

### Post by EpicWorld on 2012-01-15
Nuked all old ubuntu files and reinstalled it on an empty partition. Problem solved :3

---

