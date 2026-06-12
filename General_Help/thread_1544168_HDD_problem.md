---
title: "HDD problem"
date: 2010-08-02
forum: General Help
---

### Post by raplh on 2010-08-02
hello to all

erm im not sure how to explain this because i don't no much about computers. i did a dual boot system on my acer laptop and when i went to install the 2 operating systems i noticed that i had lost 30gb of my hard drive, i have a 320 gb hard drive and its only showing 299gb free space on hard drive and it doesn't come up with any partitions installed. now wen i tried to install windows i click by mistake the load drivers on the partition manager and saw a partition called boot on it. so my question is, is there a program that will show me hidden partitions on my hdd or a way to completely wipe me hard drive to free up the lost 30gb of space. 

am using a x64 laptop with 320gb and planning on installing windows and ubuntu as dual boot

if any body has any ideas please say all help is appreciated

---

### Post by Smart Viking on 2010-08-02
Hello, i don't know much about your problem, but most likely it is not a problem, just the way it should be, the easiest way anyhow it just to keep it how it is. But if a partition is marked as hidden you can boot up with the ubuntu live CD and mount it manually to see whats in it, this is a way you can do it:

first you must find out what the partition is called, you do that by entering this is the terminal:

```
sudo fdisk -l
```the "-l" is a little "L". when you see the partition you must find out what it is called, it might be "/dev/sda2" or maybe something else, but lets say it is called "/dev/sda4", then you can do this:

```
cd /media
```(change directory to the media folder, where you mount things)
```
sudo mkdir hidden
```the above command creates a folder named "hidden", which is where we are gona mount the partiton, now, we can go on and mount it with this command:
```
mount /dev/sda4 /media/hidden
```and now it should be mounted, now you can go to /media/hidden with the file browser and look inside the partition. :)

---

### Post by deathadder on 2010-08-02
Hi,

Your "lost" space is probably down to the fact that hard drive sizes aren't exactly correct. To make things easy some marketing people somewhere decided to make numbers rounded, so 1mb = 1000kb, 1gb = 1000 mb. While in truth 1mb = 1024kb and 1gb = 1024mb. 

The result of that being a 1gb hard drive as far as the computer is concerned is really 976mb. The difference between the hard drive size and the actual space grows as the size of the hard drive does. In the end you get sizes like so:

```

10 GB 10,000,000,000 10 GB 9.31 GB 
20 GB 20,000,000,000 20 GB 18.63 GB 
30 GB 30,000,000,000 30 GB 27.94 GB 
40 GB 40,000,000,000 40 GB 37.25 GB 
60 GB 60,000,000,000 60 GB 55.88 GB 
80 GB 80,000,000,000 80 GB 74.51 GB 
100 GB 100,000,000,000 100 GB 93.13 GB 
120 GB 120,000,000,000 120 GB 111.76 GB 
160 GB 160,000,000,000 160 GB 149.01 GB 
180 GB 180,000,000,000 180 GB 167.64 GB 
200 GB 200,000,000,000 200 GB 186.26 GB 
250 GB 250,000,000,000 250 GB 232.83 GB

```
Numbers stolen from here: [http://forum.pcmech.com/showthread.php?t=118330](http://forum.pcmech.com/showthread.php?t=118330)

---

