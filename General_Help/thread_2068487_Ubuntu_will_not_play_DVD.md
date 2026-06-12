---
title: "Ubuntu will not play DVD"
date: 2012-10-09
forum: General Help
---

### Post by sdowney717 on 2012-10-09
I do have restricted extras installed.
I tried another DVD drive

I will have to boot windows and see if there is a hardware issue.

---

### Post by thatguruguy on 2012-10-09
> **sdowney717 said:**
> I do have restricted extras installed.
I tried another DVD drive

I will have to boot windows and see if there is a hardware issue.

There's another step you have to take. Read [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

---

### Post by sdowney717 on 2012-10-09
Thanks, ok will try it. I am running windows and the DVD plays so must be a software issue.

---

### Post by GeForce 9500GT on 2012-10-09
Take a look [here]("https://sites.google.com/site/tipsandtricksforubuntu/multimedia/how-to-add-multimedia"). And especially the last tip about DVD playback might be interesting for you.

---

### Post by sdowney717 on 2012-10-09
Well it plays but all the colors are BLUE

ok goto edit menu and set hue. then it fixed the colors.

---

### Post by sdowney717 on 2012-10-09
Ha, Ha, colors are fine in VLC but not in movie player??

---

### Post by sdowney717 on 2012-10-09
can the install-css.sh program run offline on a PC with no internet access?
I have a PC on the boat running Ubuntu and want to make sure it can play DVD's.

---

### Post by GeForce 9500GT on 2012-10-09
I have 2 settings for mplayer to test for you. These 2 options you can type in a terminal.
 
setting 1:
```
mplayer -vo x11
```
setting 2:
```
mplayer -vo xover
```
 
Try them both and check with setting prevent your screen turning blue.
 
Just found a third setting to try:
```
mplayer -vo xv
```

---

### Post by sdowney717 on 2012-10-09
reinstalled offline gives error

> scott@scott-P5QC:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for scott: 
--2012-10-09 07:48:45--  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
Dynamic fetch failed; Falling back to static fetch
--2012-10-09 07:48:45--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
scott@scott-P5QC:~$ 


How can this be done off line?

---

### Post by sdowney717 on 2012-10-09
> **GeForce 9500GT said:**
> I have 2 settings for mplayer to test for you. These 2 options you can type in a terminal.
 
setting 1:
```
mplayer -vo x11
```
setting 2:
```
mplayer -vo xover
```
 
Try them both and check with setting prevent your screen turning blue.
 
Just found a third setting to try:
```
mplayer -vo xv
```

Hi, it is totem movie player doing the blue thing.

---

### Post by GeForce 9500GT on 2012-10-09
> **sdowney717 said:**
> reinstalled offline gives error..........How can this be done off line?
 
With off-line you mean not connected to the internet? To update or upgrade your system you must be connected to the internet. Each repository is only available on servers except the live-cd/dvd ofcourse. The medibuntu packages is only available at the site of Medibuntu and not local.

---

### Post by Elfy on 2012-10-09
> **sdowney717 said:**
> can the install-css.sh program run offline on a PC with no internet access?
I have a PC on the boat running Ubuntu and want to make sure it can play DVD's.

Apparently not - just unplugged and ran it.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
--2012-10-09 12:51:55--  http://packages.medibuntu.org/dists/quantal/free/binary-amd64/Packages
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
Dynamic fetch failed; Falling back to static fetch
--2012-10-09 12:51:55--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
hob@sidh:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2012-10-09 12:52:15--  http://packages.medibuntu.org/dists/quantal/free/binary-amd64/Packages
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8993 (8.8K) [text/plain]
Saving to: `/tmp/dvdcss-wh9fnZ/Packages'

100%[======================================>] 8,993       --.-K/s   in 0.05s   

2012-10-09 12:52:15 (182 KB/s) - `/tmp/dvdcss-wh9fnZ/Packages' saved [8993/8993]

--2012-10-09 12:52:15--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_amd64.deb
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 40506 (40K) [application/octet-stream]
Saving to: `/tmp/dvdcss-wh9fnZ/libdvdcss.deb'

100%[======================================>] 40,506       263K/s   in 0.2s    

2012-10-09 12:52:16 (263 KB/s) - `/tmp/dvdcss-wh9fnZ/libdvdcss.deb' saved [40506/40506]

Selecting previously unselected package libdvdcss2.
(Reading database ... 214953 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-wh9fnZ/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

you might be able to work out what you need to have installed from that and reading the script. 

I'd assume that getting the necessary packages and installing them manually would work.

---

### Post by sdowney717 on 2012-10-09
Just tried an install off line and it works.
First be online to get the deb file using wget. This will show up in your home directory

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb)

> 
scott@scott-P5QC:~$ wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb)
--2012-10-09 08:02:02--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 39684 (39K) [application/octet-stream]
Saving to: `libdvdcss2_1.2.12-0.0medibuntu1_i386.deb'

100%[======================================>] 39,684       125K/s   in 0.3s    

2012-10-09 08:02:03 (125 KB/s) - `libdvdcss2_1.2.12-0.0medibuntu1_i386.deb' saved [39684/39684]


then run this offline. It reinstalled here ok. Will test today at boat.

sudo dpkg -i libdvdcss2_1.2.12-0.0medibuntu1_i386.deb

> 
scott@scott-P5QC:~$ sudo dpkg -i libdvdcss2_1.2.12-0.0medibuntu1_i386.deb

[sudo] password for scott: 
(Reading database ... 582898 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.12-0.0medibuntu1 (using libdvdcss2_1.2.12-0.0medibuntu1_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
scott@scott-P5QC:~$ 

---

### Post by sdowney717 on 2012-10-09
also if you need to reduce the drive spin speed due to fast noisy drives,  you can do the items mentioned here.

[http://ubuntuforums.org/showthread.php?t=1905246](http://ubuntuforums.org/showthread.php?t=1905246)

the eject command has to be run for every disc insertion

the 
> Decided to try a much simpler solution:
Create the file /etc/udev/rules.d/dvd-speed.rules:
DEVNAME=="dvd", ACTION=="change", RUN+="/sbin/hdparm -E4 /dev/sr0"
or, which is more clear for the reader
DEVNAME=="dvd", ACTION=="change", RUN+="/usr/bin/eject -x 8 /dev/dvd"
idea is it will automatically do this 

I will test and see for myself.
Anyone else notice disc spins way to fast when playing DVD?

Other thought is can you put a commandline into starting VLC that when it starts up it slows down the disc?

---

