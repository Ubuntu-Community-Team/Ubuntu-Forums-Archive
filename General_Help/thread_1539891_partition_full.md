---
title: "partition full?"
date: 2010-07-27
forum: General Help
---

### Post by fahadayaz on 2010-07-27
i have UNE 10.04 LTS on my dell mini 9. 

since it only has 8gb internal storage space, i bought a microsd card (with an adapter to convert to sd card) and put that in the memory card slot. i installed ubuntu all under the one partition but thought it would be best to stick the /usr partition on the sdcard along with another partition just to store stuff on.

i used it fine for a couple of months, but then the /usr partition got full and messed up whilst trying to install packages. so using a liveusb i expanded the partition a bit using gparted to take some space from the other partition i had created. i restarted back into ubuntu.

this seemed to work fine but a couple of weeks down the line, having installed some more packages, the partition got full again. i did the same thing, expanding the partition by taking from the other. this time, however, apt-get seems not to see the extra space saying the disk is full also, it sees broken packages, since the failed package install attempts from before.

as you can see from df -h, i have 100mb free on the /usr partition.

> 
fahad@fahad-netbook:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.1G  6.0G  740M  90% /
none                  493M  288K  493M   1% /dev
none                  497M  4.9M  492M   1% /dev/shm
none                  497M  196K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/mmcblk0p1        4.2G  3.9G  106M  98% /usr
/dev/mmcblk0p2        3.1G  2.8G  177M  95% /media/home links_

whilst attempting to fix broken packages, after clicking apply, it will try for a second before displaying the following error message:

> E: /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.2_i386.deb: unable to create `/usr/bin/ldd.dpkg-new' (while processing `./usr/bin/ldd')

if i look at the terminal output, the following is displayed.... (actually it didnt let me copy it so instead i did sudo apt-get install -f in terminal.. :D)

> fahad@fahad-netbook:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
fahad@fahad-netbook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libgtk-vnc-1.0-0 pidgin-libnotify
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gtk2-engines-pixbuf gwibber gwibber-service libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libgail-common libgail18
  libgtk2.0-0
Suggested packages:
  gwibber-themes glibc-doc
The following packages will be upgraded:
  gtk2-engines-pixbuf gwibber gwibber-service libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libgail-common libgail18
  libgtk2.0-0
11 upgraded, 0 newly installed, 0 to remove and 241 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.2MB of archives.
After this operation, 65.5kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 283189 files and directories currently installed.)
Preparing to replace libc-bin 2.11.1-0ubuntu7.1 (using .../libc-bin_2.11.1-0ubuntu7.2_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.2_i386.deb (--unpack):
 unable to create `/usr/bin/ldd.dpkg-new' (while processing `./usr/bin/ldd'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.11.1-0ubuntu7.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


as you can see near the end, the apparent error is that the disk is full, which it is not. any idea what the problem might be? can i resolve this without having to reinstall ubuntu?  :(

---

### Post by thebigob on 2010-07-29
Your /usr dir is 98% u should really look to freeing up space at the very least on that partition but if im honest you cutting it very close in most of your partitions

---

### Post by bumanie on 2010-07-29
First two things to do are > sudo apt-get clean followed by > sudo apt-get autocleanTo free up some space - then look [here]("http://ubuntuforums.org/showthread.php?t=1122670") for more options/explanations.

---

### Post by fahadayaz on 2010-07-29
i had still about 100mb free though. i've just increased that by 350mb by taking from the partition next to it. 

i was just about to reinstall ubuntu since the upgrade from karmic didnt give me the me menu and I'd rather have it, now that i've tried it out on the livecd.. or is that fixable? since im not able to add anything to the panel i cant see how i could. i did try deleting the .gnome, .gnome2, .gconf folders in my home directory

---

