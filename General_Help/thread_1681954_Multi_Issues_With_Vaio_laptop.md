---
title: "Multi Issues With Vaio laptop"
date: 2011-02-05
forum: General Help
---

### Post by SuislideX on 2011-02-05
Ok .. So hi ... Well Lets get to bare bones here..
I have a sony vaio laptop model vpcf115fm : Hardware includes i7 q 720 @1.6ghz, Nvidia GeForce GT 330m, My screens resolution is 1920x 1080 60Hz Running WIndows 7 64bit on most programs that are available.
...
...
Ok no my issues When trying to install Ubunto 10.10 64bit on my machine. I do only get there I dont get the selected option in this screen. [http://www.ubuntu.com/sites/default/files/active/maverick/install_03_medium.jpg](http://www.ubuntu.com/sites/default/files/active/maverick/install_03_medium.jpg)
... So from there Specify Partitions which i made a unallocated partition with 70gb ... The four partitions there are
1} 8.66 GB Healthy (Recovery Partition)
2} System Reserved 100MB Healthy (System, Active, Primary Partition)
3} (C:) 383.75 GB NTFS  Healthy (Boot, Page File, Crash Dump, Primary Partition)
4} 73.24GB Unallocated <where I want Ubuntu>

..Ok So yeah I set number 4 as root ..but it wants a swap partition ... And then eventually it crashes.. So Im gonna try again now .. see what happens  But if anybody has experience here.
 The other issue Is the nvidia driver is thinking that I have a much larger screen then i do..(which I thin will be remedied when I load it up good)
Will deff be on here more.. I love linux ..Just finally trying to do it myself on my own laptop..So Thanks

---

### Post by coldraven on 2011-02-05
Boot up with your Ubuntu Desktop CD and select "Try Ubuntu"
Run System>Administration>Gparted
Select the unallocated space then right click and create a new partition about 9.5GB less than the 73GB leaving the space at the "end". (Right hand side)
Format it to EXT4.
Select the 9.5GB space and create a Linux Swap partition.
Then try the install again.

The Swap should be about double your memory. I have 4GB memory and a 9.48GB swap which was created automatically by the installer

---

### Post by tredegar on 2011-02-05
I have a sony VPCF11C5E
It was quite a performance to get linux running on it, but [this site]("https://code.google.com/p/vaio-f11-linux/issues/list?can=1&q=&colspec=ID+Type+Status+Priority+Milestone+Owner+Summary&cells=tiles") was very helpful.

---

