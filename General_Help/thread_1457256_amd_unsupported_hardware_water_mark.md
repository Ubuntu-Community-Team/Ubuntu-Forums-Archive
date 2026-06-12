---
title: "amd unsupported hardware water mark"
date: 2010-04-18
forum: General Help
---

### Post by unrealseal on 2010-04-18
have ubuntu 9.10 instaled and running fine but have the amd unsupported water mark, is there any way of removing this, graphics card is a 5770, down loaded the drivers but can't reinstall as i need to login as root, tried the sudo user name in the terminal but driver install says i,m not logged in as superuser :confused:

tried the advise but still ended up with the watermark, finally solved the problem when i upgraded to 10.04, water mark has now gone

---

### Post by Kai Summers on 2010-04-18
Login as root, but first you have to set the root password basically  open terminal type:
```
sudo root passwd
```Type your password for sudo, then terminal will ask you to enter a new  root password twice. DON'T FORGET IT!!!

At the login screen you can now click other and login as root with all  the privs. Backup all files that you are modding as a f*** up here could  break your box.

---

### Post by quadproc on 2010-04-18
> **unrealseal said:**
> have ubuntu 9.10 instaled and running fine but have the amd unsupported water mark, is there any way of removing this, graphics card is a 5770, down loaded the drivers but can't reinstall as i need to login as root, tried the sudo user name in the terminal but driver install says i,m not logged in as superuser :confused:
First thing, since you have installed the driver then you will need to remove it before installing again.  Look in /usr/share/ati for fglrx-uninstall.sh and run that to uninstall.

If you downloaded the new driver from AMD and saved it on your system then ```
cd <directory_where_downloaded_file_resides>
chmod +x <name_of_downloaded_file>
sudo sh <name_of_downloaded_file> --keep --install
```should unpack all of the files needed, place them in the right places, and start up the ATI installation program.  When you are finished and everything works then you can remove all of the files left behind by the process.

I have found that the Hardware Drivers utility does not correctly report the status of my system.  It says that the driver is not in use although the driver _is_ in use.  I don't pay attention to that utility any more.

quadproc

---

### Post by Sef on 2010-04-18
If you do need to log in as root, then follow this [tutorial]("http://ubuntuforums.org/showthread.php?t=716201").

---

