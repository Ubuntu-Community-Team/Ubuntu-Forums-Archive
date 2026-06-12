---
title: "AsRock core 100 HT IR remote"
date: 2010-10-27
forum: General Help
---

### Post by djmrsmith on 2010-10-27
Im in ubuntu 10.10
running movida/elisa 1.0.9
Im running dualboot with w7
w7 the remote works perfect.
In ubuntu i cant get it working.

Can someone please help me?
Model nr remote:TSGV-IR01

below is dmesg output
```

[ 1230.732884] lirc_dev: IR Remote Control driver registered, major 250 
[ 1230.755148] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[ 1230.758158] lirc_serial: port existence test failed, cannot continue
[ 1247.518240] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[ 1247.521256] lirc_serial: port 03f8 already in use
[ 1247.521262] lirc_serial: use 'setserial /dev/ttySX uart none'
[ 1247.521265] lirc_serial: or compile the serial port driver as module and
[ 1247.521269] lirc_serial: make sure this module is loaded first
```

---

### Post by djmrsmith on 2010-10-28
Anybody please ..... i dont want to revert back to windoze

---

### Post by yoma1977 on 2010-12-11
I have the same problem.
Tried the install routine on Asrock's pages, but never got it working + get errors when running the normal update procedure (it reverts the changes done by installing the drivers)

---

### Post by yoma1977 on 2010-12-16
Well i got it up and running now!
 
The problem is: don't ask me how (i'm a total linux noob). I was trying to solve another problem with messages in my logs and deceided to follow a guide to build and install a new kernel. 
[http://lordsithtech.net/?p=2015](http://lordsithtech.net/?p=2015)
 
Afterwards I figured i'd go and retry installing the drivers according the asrock manual, but this time it somehow worked! (i still got dpkg errors when installing the driver, but it does work)
 
Installing the driver is one thing, figuring out how to make lirc work is another :p
 
So far it's starting to shape up, being able to launch rythmbox/vlc and shutting down the pc. (i still have to find a way to launch vlc not being root and lots of other issues)
 
Bottom line: don't give up, if i can manage it i'm pretty sure you can too!
Other then that: this little asrock box is a great mini homeserver/HTPC!

---

### Post by yoma1977 on 2010-12-21
After ubuntu updates gave me a new kernel, the driver stopped working.
Here's how i got it back up:
 
1) [http://www.asrock.com/Nettop/download.asp?Model=Core 100HT&o=Linux](http://www.asrock.com/Nettop/download.asp?Model=Core 100HT&o=Linux)
1) follow the installation guidelines in the pdf supplied by asrock, install lirc, install driver (which will give you an errormessage), install the driver source (which also gave me error messages)
 
2) follow the guidelines 
 
cd /usr/src
sudo dkms remove –m lirc –v 0.8.7~pre3 --all
sudo dkms add –m lirc –v 0.8.7~pre3
sudo dkms build –m lirc –v 0.8.7~pre3
sudo dkms install –m lirc –v 0.8.7~pre3 --force
 
DO NOT TRY TO DO sudo dpkg-reconfigure lirc
 
3) reboot
 
4) doubleclick the lirc-nct677x-1.1.0-ubuntu10.10-kernel2.6.35.deb file
   (it will yet again give you an errormessage)
 
5) sudo dpkg-reconfigure lirc (without step 3 & 4 the nuvoton driver was not selectable in lirc on my system)
6) select the nuvoton driver 
7) reboot the system or restart lirc.
8) test with the irw command in a terminal if you can get your remote's commands.

---

### Post by jurg99 on 2011-07-06
hello 
I tried to install the drivers for IR Remote with ubuntu 10.10 no way.

then i installed ubuntu 11.04 som butons with the IR remote are working witout any installation. how can i programm all butons.

fromm switzerland

---

