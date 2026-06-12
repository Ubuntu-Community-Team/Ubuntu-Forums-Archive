---
title: "Main problem for me with Ubuntu"
date: 2011-02-01
forum: General Help
---

### Post by FahadMKS on 2011-02-01
One of the serious problem I seem to have with the Ubuntu is that, I am not able to play the original VCD's with ubuntu using any of the players.
The problem is that these cd's have copyright protection enabled, but I could play the cd's with the windows OS but not with ubuntu.

The error is get is that you do not have enough permission.
I do not want to edit or copy the file, just want to see it.

The CD is a video cd of a movie.

Please help me with the issue guys.

Note: I had also tried to run by logging in as Root.

---

### Post by hwttdz on 2011-02-01
It looks like vlc will run it (as it will most things) [http://wiki.videolan.org/VCD](http://wiki.videolan.org/VCD) , have you tried this?  Are you getting a specific error? Sometimes encryption needs to be turned on.

Also, it's probably never a good idea to log in as root.  And you should never use root to do something that a user has permissions to do.  i.e. a user can edit text files in their home directory, so don't use root to edit a file in your home directory.

---

### Post by uRock on 2011-02-01
You need to install libdvdcss2 in order to decrypt the movie.

For 32bit system use these two commands in a terminal,
> ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
```then
```
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

For 64bit use,
> ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```then```
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```


Cheers,
uRock

---

### Post by FahadMKS on 2011-02-01
> **hwttdz said:**
> It looks like vlc will run it (as it will most things) [http://wiki.videolan.org/VCD](http://wiki.videolan.org/VCD) , have you tried this?  Are you getting a specific error? Sometimes encryption needs to be turned on.

Also, it's probably never a good idea to log in as root.  And you should never use root to do something that a user has permissions to do.  i.e. a user can edit text files in their home directory, so don't use root to edit a file in your home directory.
I have tried with the VLC also and it also is not working.

---

### Post by FahadMKS on 2011-02-01
> **uRock said:**
> You need to install libdvdcss2 in order to decrypt the movie.

For 32bit system use these two commands in a terminal,


For 64bit use,



Cheers,
uRock

The issue still seems to be there.
the file is in .dat format.

---

### Post by uRock on 2011-02-01
Here is what someone else did to be able to play .dat files. [http://www.thinkdigit.com/forum/open-source/36799-how-play-vcd-dat-files-ubuntu.html](http://www.thinkdigit.com/forum/open-source/36799-how-play-vcd-dat-files-ubuntu.html)

---

### Post by FahadMKS on 2011-10-29
Will try with the steps you gave and will inform the status shortly.

---

### Post by 3rdalbum on 2011-10-29
Play the VCD using the "Play Disc" function of VLC or Totem Movie Player. Don't just try to play the ".dat files" - they are not actually files on a disc so you can't play them as though they were.

---

