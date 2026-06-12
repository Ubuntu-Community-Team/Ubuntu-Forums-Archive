---
title: "Putting ubuntu on an old pc"
date: 2012-08-09
forum: General Help
---

### Post by Zirts on 2012-08-09
And the problem is that it has windows xp on it currently and it contains a worm virus.

I need to backup some pictures and stuff on a USB stick when I do the changeover. Thing is that the USB stick is a bit messy and I cannot risk having thoes files on it for a long time so I have to put them on my own laptop for that long.

Laptop is using Win 7, is the risk big?  I mean can I get infected with the worm while swapping?

---

### Post by albandy on 2012-08-09
Boot the computer with linux in live mode, backup the files to the USB stick using tar.gz or tar.bz2 and copy that file to your laptop.

For example:
```

sudo tar zcvf /media/usb_stick/backup.tgz /media/windows_hard_disk/the_folder_I_want_to_backup 

```

---

### Post by mastablasta on 2012-08-09
> **Zirts said:**
> And the problem is that it has windows xp on it currently and it contains a worm virus.
 
I need to backup some pictures and stuff on a USB stick when I do the changeover. Thing is that the USB stick is a bit messy and I cannot risk having thoes files on it for a long time so I have to put them on my own laptop for that long.
 
Laptop is using Win 7, is the risk big? I mean can I get infected with the worm while swapping?
 
if you will move files from WindowsXP to windows 7 you will also move the virus. 
 
however you can run ubuntu form USB, install antivirus on it and then clean the winXP mashcine with it.

---

### Post by Kalanac on 2012-08-09
Or use ClamAV in Linux to clean the files you're moving.  Linux won't catch the worm, both because it's a windows virus and because Linux is generally robust against viruses.

---

### Post by ranger1021994 on 2012-08-09
> **Zirts said:**
> And the problem is that it has windows xp on it currently and it contains a worm virus.

I need to backup some pictures and stuff on a USB stick when I do the changeover. Thing is that the USB stick is a bit messy and I cannot risk having thoes files on it for a long time so I have to put them on my own laptop for that long.

Laptop is using Win 7, is the risk big?  I mean can I get infected with the worm while swapping?

1> Boot from LiveCD or liveUSB
2> Copy your important files
3> Install ClamAV on Ubuntu (liveCD or liveUSB) and clean your Windows drives

---

### Post by mastablasta on 2012-08-09
first clean the infected files, then copy.
 
ofcourse it's another issue if you have a rootkit.

---

