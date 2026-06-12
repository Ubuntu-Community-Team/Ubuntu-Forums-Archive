---
title: "Ubuntu 12.04 - No Encrypted DVD Playback (libdvdcss2 installed)"
date: 2012-04-28
forum: General Help
---

### Post by Michele S on 2012-04-28
Hello, i installed the libdvdcss2 library to play encrypted DVD's but the playback still doesn't work.

This is the comand i used:

sudo /usr/share/doc/libdvdread4/install-css.sh 

If i try to install libdvdcss2 from apt-get it says that is already installed.

---

### Post by Michele S on 2012-04-28
Solved this with:

```
sudo apt-get install regionset

sudo regionset /dev/sr0/

```After set region to "2" and removing ~/.dvdcss/ directory the DVD played well.

---

### Post by mdacova on 2012-05-01
> **Michele S said:**
> Hello, i installed the libdvdcss2 library to play encrypted DVD's but the playback still doesn't work.

This is the comand i used:

sudo /usr/share/doc/libdvdread4/install-css.sh 

If i try to install libdvdcss2 from apt-get it says that is already installed.


thanks fixed mine

---

### Post by blknite on 2012-10-01
Thanks -- worked for me too.

---

