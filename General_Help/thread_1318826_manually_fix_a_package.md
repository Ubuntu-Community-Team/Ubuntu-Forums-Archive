---
title: "manually fix a package"
date: 2009-11-07
forum: General Help
---

### Post by ryon341 on 2009-11-07
I have a ubuntu 9.10, newly installed.  I cannot load any software either from the software center or via a downloaded .deb file.   In the terminal I receive the following message:

"I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package."

I have read other posts and have attempted several things:

sudo aptitude update
sudo aptitude -f install
sudo aptitude clean
sudo aptitude purge adobe-flashplugin
sudo aptitude -reinstall

I have attempted dowloading the .deb file from adobe and receive the following error when installing:

Could not open install_flash_player_10_linux.deb.  the package might be corrupted or you are not allowed to open the file.  Check the permissions on the file.

I am logged in as root and I have downloaded the file multiple times.

Can anyone provide a solution for this?

---

### Post by pastalavista on 2009-11-07
Open System-> Administration-> Software Sources and check all the boxes on the first tab. Then run ```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

Also, you never need to "login as root" just precede the command with sudo or, for graphical apps, use gksu.

---

### Post by ryon341 on 2009-11-07
I fixed it.  I found another post/thread with an identical problem.  thanks.

---

### Post by aznsmartj0ck on 2009-11-09
I'm having the exact same problem...flash works with everything except firefox...can somebody please tell me how to get it to work?  Thanks

---

