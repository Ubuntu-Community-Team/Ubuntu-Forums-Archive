---
title: "Wpa-psk / Ipw2200 ?!"
date: 2006-04-26
forum: General Help
---

### Post by vladimir-dk on 2006-04-26
Im getting stucked in this how-to:
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

```
danny@laptop:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```
```
danny@laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
danny@laptop:~$

```
```
danny@laptop:~$ sudo apt-get install linux-headers-2.6.12-10-386
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-10-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
danny@laptop:~$

```

I downloaded these three
- ieee80211-1.1.13
- ipw2200-1.1.2
- ipw2200-fw-2.3

I unzip the subsystem and run the remove-old sh script and then the make file.
```
danny@laptop:~/Files/Temp/netkort WLAN/sub/ieee80211-1.1.13$ sudo make
/bin/sh: /home/danny/Files/Temp/netkort: No such file or directory
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:

    % sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1
danny@laptop:~/Files/Temp/netkort WLAN/sub/ieee80211-1.1.13$

```

I read the forum and found out that the script dosnt remove the old drivers automatically and i tried to find the old drivers like this
```
danny@laptop:~$ sudo find /lib/modules/2.6.12-10-386/ -name 'ipw*'
danny@laptop:~$

```
and
```
danny@laptop:~$ sudo find /lib/modules/2.6.12-10-386/ -name 'ieee80211*'
danny@laptop:~$

```

But I cant find the rest of the old drivers anywhere. Im quite new to the linux filesystem and dont know how to solve this issue. Ive search google for days and cant find the right information. I read all the post in the how-to that luca_linux created and found some people with the same problem and thet solved it by removing them manually with File Browser (root) or "rm -r". But Im not haveing any luck.

Can some guide me pass this?

---

### Post by vladimir-dk on 2006-04-27
Can anyone give me a hint? Any suggestions is appriciated.

---

### Post by nilezon on 2006-05-05
I'm having same problems, but no solution ... yet...

Edit:
Downloading latest version of IEEE80211 helped me ...
[http://ieee80211.sourceforge.net/downloads.php]("http://ieee80211.sourceforge.net/downloads.php")

---

### Post by Ginger The Cat on 2006-05-05
Have you looked at [http://www.goldfisch.at/knowledge/337](http://www.goldfisch.at/knowledge/337) ?

I found that the more recent remove-old works perfectly so I don't need to go through all that searching for old modules.

All I do now is

cd ieee802.<whatever>
sudo sh remove-old
cd ..

cd ipw2200-<whatever>
sudo sh remove-old
cd ..

cd ieee.<whatever>
make
sudo make install
cd ..

cd ipw.<whatever>
make
sudo make install

reboot

Mike

---

