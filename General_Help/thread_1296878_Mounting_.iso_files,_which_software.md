---
title: "Mounting .iso files, which software ?"
date: 2009-10-21
forum: General Help
---

### Post by simartem on 2009-10-21
Hi,
 
I have switched to Ubuntu recently, and i am not very familiar with this OS.. I love it very much and still learning day by day.. I want to know what is the **Linux alternatives** of softwares such as _"Daemon Tools"_ (in windows) and/or _MagicISO_ (in windows) to mount my DVD image files.. Any links or suggestions are appreciated. Thank you very much

---

### Post by diaco on 2009-10-21
I use GMount ISO
[https://launchpad.net/gmount-iso](https://launchpad.net/gmount-iso)
[http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/](http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/)

---

### Post by DeMus on 2009-10-21
> **simartem said:**
> Hi,
 
I have switched to Ubuntu recently, and i am not very familiar with this OS.. I love it very much and still learning day by day.. I want to know what is the **Linux alternatives** of softwares such as _"Daemon Tools"_ (in windows) and/or _MagicISO_ (in windows) to mount my DVD image files.. Any links or suggestions are appreciated. Thank you very much

Mount and unmount Iso-files

Using Nautilus Scripts
First we have to download two scripts, one to mount an ISO file and one to un-mount an ISO file.
The two scripts can be downloaded here:
Script to mount a file: [_here_]("http://www.debianadmin.com/images/iso/mount.sh")
Script to un-mount a file: [_here_]("http://www.debianadmin.com/images/iso/unmount.sh")
Download them to the normal folder you always use to download files.
Once you have these two scripts you need to change the permissions using the following commands
Open a terminal.  To do this click Applications > Accessories > Terminal
Type ```
cd name/of/downloadfolder
``` (e.g. Downloads)
```
sudo chmod +x mount.sh
```
```
sudo chmod +x unmount.sh
```
Now you need to move the 2 nautilus scripts to the right folder:
```
sudo mv mount.sh ~/.gnome2/nautilus-scripts/
sudo mv unmount.sh ~/.gnome2/nautilus-scripts/
```

From now on when you right click an iso file you get an option in your drop down menu to mount or unmount the iso file.


Oops: I just saw that there is something wrong with the Debian webpages to download the scripts from. The pages don't seem to work.
If you are interested in the scripts I can mail them you, just send me a personal message.

---

### Post by dominiquec on 2009-10-21
You can just double-click on the ISO file and it will automatically mount.  You can also right-click on the file: that will give you other options like extracting files.

---

### Post by John Bean on 2009-10-21
> **dominiquec said:**
> You can just double-click on the ISO file and it will automatically mount.  You can also right-click on the file: that will give you other options like extracting files.

Just what I was about to write :-)

---

### Post by simartem on 2009-10-21
Thanks everybody for rapid answers and help.. Regards

---

### Post by linux-hack on 2009-10-21
in linux you can mount .iso files with the mount command exactly like a HDD.

---

