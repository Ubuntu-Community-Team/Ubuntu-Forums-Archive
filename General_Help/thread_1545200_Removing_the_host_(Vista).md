---
title: "Removing the host (Vista)"
date: 2010-08-03
forum: General Help
---

### Post by Dj Seraph on 2010-08-03
Hey i resently install Ubuntu wubi. So how do i remove the Vista ?? 
Bad english :(

---

### Post by sikander3786 on 2010-08-03
Hi.

It is not possible to uninstall the host and save the guest OS because most probably Ubuntu is installed on the same partition as Vista.

The best way around will be to backup your Ubuntu install with any backup software like Clonezilla, and then use it to restore Ubuntu on a dedicated partition but that will of course require some expertise.

If you don't have lots of software installed and configuration on you Ubuntu machine, go with a new fresh dedicated install after removing Vista.

Regards.

---

### Post by JustinR on 2010-08-03
> **sikander3786 said:**
> Hi.

It is not possible to uninstall the host and save the guest OS because most probably Ubuntu is installed on the same partition as Vista.

The best way around will be to backup your Ubuntu install with any backup software like Clonezilla, and then use it to restore Ubuntu on a dedicated partition but that will of course require some expertise.

If you don't have lots of software installed and configuration on you Ubuntu machine, go with a new fresh dedicated install after removing Vista.

Regards.

You can migrate Wubi to a native partition though - [http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/](http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/)

---

### Post by sikander3786 on 2010-08-03
> **JustinR said:**
> You can migrate Wubi to a native partition though - [http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/](http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/)

Yeah that might be possible but I don't think it will work every time it is performed. A fresh install is recommended in almost all cases.

---

### Post by bcbc on 2010-08-03
> **JustinR said:**
> You can migrate Wubi to a native partition though - [http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/](http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/)

That script doesn't work on 10.04 (or 9.10). It references commands no longer available and installs grub-legacy. I have an updated version [here]("http://ubuntuforums.org/showthread.php?t=1519354").

In any case it requires that you migrate to a different partition than the one holding the wubi root.disk. But I recommend keeping both vista and wubi until you are sure the migration is successful - so the best bet is to shrink your vista partition, migrate the wubi to the new partition, and then when you are happy, reuse the vista partition later - perhaps as a separate /home partition.

Since you recently installed wubi, it may be simpler just to reinstall a fresh ubuntu over vista, after backing up any important data.

---

### Post by Dj Seraph on 2010-08-04
The new one dosnt work =(  My Ubuntu is gone, using vista again.
Downloading the Ubuntu again, 699 MB takes time.........

---

### Post by bcbc on 2010-08-04
> **Dj Seraph said:**
> The new one dosnt work =(  My Ubuntu is gone, using vista again.
Downloading the Ubuntu again, 699 MB takes time.........

What happened? What did you do and how did Ubuntu disappear?

---

### Post by Dj Seraph on 2010-08-04
Its dosnt appear in my new partition thingy, i cannot even use dual boot to start ubuntu.
i cannot remember what the words but its fails.  The guide you guys game me works but the last thing i do im command line dosnt appear to work proper on my laptop .

Anyway i have install the new one and remove vista,  works fine now :p I ll come back and giva ya update on this one

---

### Post by Dj Seraph on 2010-08-04
So everything went well in installation, Vista is gone too. no problem here, 
thanks guys

---

