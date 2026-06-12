---
title: "How to completely switch to ubuntu from vista after wubi"
date: 2011-08-27
forum: General Help
---

### Post by robbv1122 on 2011-08-27
I've been using ubuntu for about a month now and i'm sold. I installed  ubuntu 11.04 using wubi and now i want to make ubuntu the default system  without erasing my data. 

I also want create a new partition  allocating more space for ubuntu. I think if i accomplished my first  task i will be able to do this easier. Thanks in advance!

---

### Post by tmette on 2011-08-27
Just download a copy of the Ubuntu ISO that you want.  Then burn it to a CD and boot from it.  The installer is actually quite nice and simple, and can partition the HDD for you.

Just make sure to install the GRUB onto the windows partition so that it will ask you on startup, which OS to load.

I would still recommend backing up your Vista files in case anything goes wrong and you have to start over.  :)

---

### Post by robbv1122 on 2011-08-28
> **tmette said:**
> Just download a copy of the Ubuntu ISO that you want.  Then burn it to a CD and boot from it.  The installer is actually quite nice and simple, and can partition the HDD for you.

Just make sure to install the GRUB onto the windows partition so that it will ask you on startup, which OS to load.

I would still recommend backing up your Vista files in case anything goes wrong and you have to start over.  :)

Thanks for the reply. I backed up my data already. If i downloaded ubuntu ISO from a CD would i be able to keep my data from wubi. I like the way I've personalized it. Or would i just have to start from scratch again.

---

### Post by bcbc on 2011-08-28
[HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by robbv1122 on 2011-08-28
> **bcbc said:**
> [HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

This assumes that i have the partition already created. I've been having a very hard time do this with Gparted and Windows disk manager. Would it be easier if i just i deleted wubi and started from scratch, install ubuntu ISO from CD.

---

### Post by oldfred on 2011-08-28
Most Win7 systems use all 4 primary partitions, so it becomes difficult to create the extended partition to install Ubuntu's / (root), swap and possibly /home partitions.

Do not create partitions with windows as it converts to a proprietary LVM or dynamic partitions which are not compatable with anything including some of windows repair tools.

Be sure to have good backups and make a windows repairCD.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by ninjaaron on 2011-08-28
If you backup your home-folder, most of the settings files will be save.  You will have to download apps over again, but I don't find this to be such a big deal.  I believe it is even possible to get Synaptic to write a script for you to automatically bring back all of your old programs, but I'm not sure how this is done, as I write my own post-install scripts.

---

### Post by oldfred on 2011-08-28
+1 on ninjaaron suggestion to backup /home as that has your data and in hidden files & folders all your user settings.

You can list packages this way.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

