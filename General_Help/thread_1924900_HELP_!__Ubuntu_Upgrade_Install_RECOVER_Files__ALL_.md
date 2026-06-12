---
title: "HELP !  Ubuntu Upgrade Install RECOVER Files ? ALL DATA FILES LOST"
date: 2012-02-13
forum: General Help
---

### Post by imf2012 on 2012-02-13
HELP. Re Installed Ubuntu Upgrade to 11.10 from v10 today using download burnt image from Ubuntu.com
LOST ALL FILES eg photos, music docs etc. Does anyone know if there is any way to RECOVER FILES 
Option to install Ubuntu and KEEP ALL AFILES was selected but GONE !!
Ubuntu User but do not know internals Ian
:(

---

### Post by wyliecoyoteuk on 2012-02-13
First, check in the home directory, to see if there is more than one user directory, your files may be there, just under a different name.
(Had this happen ages ago, when I input the wrong user name)

---

### Post by JC Cheloven on 2012-02-13
If you don't know how to proceed with wyliecoyoteuk advice, please start opening a terminal and letting us know the output of these comands (one at a time; you can copy-paste from here):
```
ls -al /home
ls -al ~
```

---

### Post by imf2012 on 2012-02-13
Looking in Home from eg places All my files dont show just new empty folders for music , pictures , docs etc

---

### Post by imf2012 on 2012-02-13
Used to know where to find terminal prompt to enter command in V10
Now
In V 11 Dont know how to get Terminal prompt up !!!!

---

### Post by JC Cheloven on 2012-02-13
> **imf2012 said:**
> Used to know where to find terminal prompt to enter command in V10
Now
In V 11 Dont know how to get Terminal prompt up !!!!

Please press Ctrl-Alt-T and a terminal should pop up.

---

### Post by Yellow Pasque on 2012-02-13
You can't upgrade from 10.x to 11.10. You most likely did a fresh install and formatted the disk. I hope you have a backup..

---

### Post by imf2012 on 2012-02-14
ls -al /home 
gives
elvis2012@elvis2012-VGN-NS10J-S:~$ ls -al /home
total 20
drwxr-xr-x  5 root      root      4096 2012-02-13 16:09 .
drwxr-xr-x 25 root      root      4096 2012-02-13 16:20 ..
drwxr-xr-x  4 root      root      4096 2012-02-13 16:09 .ecryptfs
drwx------ 26 elvis2012 elvis2012 4096 2012-02-14 12:41 elvis2012
dr-x------  3 elvis2012 elvis2012 4096 2010-07-24 22:22 imf
elvis2012@elvis2012-VGN-NS10J-S:~$ ^C

does not look promising

ls al ~

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

elvis2012@elvis2012-VGN-NS10J-S:~$ ls -al /home
total 20
drwxr-xr-x  5 root      root      4096 2012-02-13 16:09 .
drwxr-xr-x 25 root      root      4096 2012-02-13 16:20 ..
drwxr-xr-x  4 root      root      4096 2012-02-13 16:09 .ecryptfs
drwx------ 26 elvis2012 elvis2012 4096 2012-02-14 12:41 elvis2012
dr-x------  3 elvis2012 elvis2012 4096 2010-07-24 22:22 imf
elvis2012@elvis2012-VGN-NS10J-S:~$ ^C
elvis2012@elvis2012-VGN-NS10J-S:~$ ^C
elvis2012@elvis2012-VGN-NS10J-S:~$ ^C
elvis2012@elvis2012-VGN-NS10J-S:~$ ls -al ~
total 252
drwx------ 26 elvis2012 elvis2012  4096 2012-02-14 12:41 .
drwxr-xr-x  5 root      root       4096 2012-02-13 16:09 ..
drwx------  3 elvis2012 elvis2012  4096 2012-02-13 19:41 .adobe
-rw-r--r--  1 elvis2012 elvis2012   220 2012-02-13 16:09 .bash_logout
-rw-r--r--  1 elvis2012 elvis2012  3353 2012-02-13 16:09 .bashrc
drwx------ 13 elvis2012 elvis2012  4096 2012-02-13 20:07 .cache
drwxrwxr-x  3 elvis2012 elvis2012  4096 2012-02-13 19:29 .compiz-1
drwx------ 12 elvis2012 elvis2012  4096 2012-02-13 19:39 .config
drwx------  3 elvis2012 elvis2012  4096 2012-02-13 19:03 .dbus
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Desktop
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Documents
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Downloads
lrwxrwxrwx  1 elvis2012 elvis2012    35 2012-02-13 16:09 .ecryptfs -> /home/.ecryptfs/elvis2012/.ecryptfs
-rw-------  1 elvis2012 elvis2012    16 2012-02-13 19:03 .esd_auth
-rw-r--r--  1 elvis2012 elvis2012   179 2012-02-13 16:09 examples.desktop
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:11 .fontconfig
drwx------  4 elvis2012 elvis2012  4096 2012-02-14 12:40 .gconf
drwx------  4 elvis2012 elvis2012  4096 2012-02-13 19:03 .gnome2
-rw-rw-r--  1 elvis2012 elvis2012   157 2012-02-14 12:41 .gtk-bookmarks
dr-x------  2 elvis2012 elvis2012     0 2012-02-14 12:40 .gvfs
-rw-------  1 elvis2012 elvis2012  1512 2012-02-14 12:40 .ICEauthority
drwxrwxr-x  3 elvis2012 elvis2012  4096 2012-02-13 19:11 .libreoffice
drwxrwxr-x  3 elvis2012 elvis2012  4096 2012-02-13 19:03 .local
drwx------  3 elvis2012 elvis2012  4096 2012-02-13 19:41 .macromedia
drwx------  3 elvis2012 elvis2012  4096 2012-02-13 19:03 .mission-control
drwx------  4 elvis2012 elvis2012  4096 2012-02-13 19:11 .mozilla
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Music
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Pictures
lrwxrwxrwx  1 elvis2012 elvis2012    34 2012-02-13 16:09 .Private -> /home/.ecryptfs/elvis2012/.Private
-rw-r--r--  1 elvis2012 elvis2012   675 2012-02-13 16:09 .profile
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Public
drwx------  2 elvis2012 elvis2012  4096 2012-02-14 12:40 .pulse
-rw-------  1 elvis2012 elvis2012   256 2012-02-13 19:03 .pulse-cookie
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Templates
drwx------  5 elvis2012 elvis2012  4096 2012-02-13 19:39 .thumbnails
drwxr-xr-x  2 elvis2012 elvis2012  4096 2012-02-13 19:03 Videos
-rw-------  1 elvis2012 elvis2012    66 2012-02-14 12:40 .Xauthority
-rw-------  1 elvis2012 elvis2012 27518 2012-02-14 12:45 .xsession-errors

looks like all is lost
except for stuff on flashdrive or in windows partn !!

---

### Post by winh8r on 2012-02-14
If you have accidentally deleted any data and you wish to recover it, then it is important that you stop using that computer as soon as possible after you realise your mistake. This will give you a better chance of recovering data successfully.

There are a variety of tools to recover data available today. One of the simplest and best is the Testdisk/Photorec suitewhich can be installed by opening a terminal and typing 

```
sudo apt-get install testdisk
```


There is a step by step guide to using the program available at


[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

Please take some time to read about the product and what it does before deciding if it is right for your specific situation. If you do not understand something, read the manual again, and then ask someone you trust for advice. Data recovery is not an instant process, in some cases, depending on the size of the disk/amount of data to be recovered the time required for data recovery can run into days. So make sure that you have an alternative to using the affected computer/drive/device before starting any data recovery.

Once it is running, let it run! Don't be tempted to keep checking to see what it has recovered. If you allow it to have full resources to run it will run more efficiently and successfully.

If you have deleted one single file that you wish to recover, ensure that you set the parameters of the program to only recover files of that type during recovery, this will speed up the process.

---

### Post by drmrgd on 2012-02-14
It looks like you may have formatted and lost everything during the install.  The lesson learned here is to always make backups of your important stuff before attempting any major system change (like an upgrade).  

Moving forward, though, follow Winh8r's advice and you may be able to recover at least some of the lost data.

---

### Post by imf2012 on 2012-02-14
OK have replaced most files from elsewhere.

Thanks for help
everyone 
JC Chelovan
Wyliecoyoteuk
Winh8r
drmrgd

May try testdisk

---

