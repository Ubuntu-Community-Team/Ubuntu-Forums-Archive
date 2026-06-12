---
title: "Home on other harddrive"
date: 2012-06-05
forum: General Help
---

### Post by Sinopa on 2012-06-05
Hi.

Does anyone know how I can move /home to another harddrive?
I use a small 120Gb SSD for system, but it doesn't have enough space for home and all the files I have in home :)

If anyone know of a good, easy to understand tuts I would be very happy :)

---

### Post by oldfred on 2012-06-05
This is good for moving /home to another partition, does not matter where.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But I prefer to leave /home inside / on the SSD so user settings are still loaded quickly. But I move all data folders like Documents, Videos, Music etc to a data partition. I mount data partition in /mnt/data and link the folders back to /home so it still looks like a standard install but all the data is in a partition on the rotating drive.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion - linking or using bind:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by gordintoronto on 2012-06-05
Oldfred: is there a simple method I could use to move Music, for example, to another partition? What is the minimum number of steps?

---

### Post by traditionalist on 2012-06-05
I just put /  on the SSD  and /home on one of my other drives;

[[IMG]http://img407.imageshack.us/img407/394/informationaboutdevsdc1.th.png[/IMG]]("http://img407.imageshack.us/i/informationaboutdevsdc1.png/")

[[IMG]http://img256.imageshack.us/img256/8755/informationaboutdevsda1.th.png[/IMG]]("http://img256.imageshack.us/i/informationaboutdevsda1.png/")

I found the easiest way to redirect the folders was this;

[[IMG]http://img140.imageshack.us/img140/5302/ubuntutweak001.th.png[/IMG]]("http://img140.imageshack.us/i/ubuntutweak001.png/")

[[IMG]http://img403.imageshack.us/img403/5302/ubuntutweak001.th.png[/IMG]]("http://img403.imageshack.us/i/ubuntutweak001.png/")

this is what you see and can access when SDA1 is mounted, you can set it to automount;

[[IMG]http://img690.imageshack.us/img690/7451/sda1data001.th.png[/IMG]](http://img690.imageshack.us/i/sda1data001.png/)

---

