---
title: "Software Center - Disk Full Error"
date: 2012-10-10
forum: General Help
---

### Post by suspended on 2012-10-10
There is a lot that I am learning about Ubuntu still and need some help with the following situation.
 
I purchased from the Software System (my first purchase) the Sacred Gold game. It was a 2.1GB download. Which is huge and took quite a while to download. 
 
However, after it downloaded and began the install process I came across this error:
```
[COLOR=black][FONT=Verdana]installArchives() failed: [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ...  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 5% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 10% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 15% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 20% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 25% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 30% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 35% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 40% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 45% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 50% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 55% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 60% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 65% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 70% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 75% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 80% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 85% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 90% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 95% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 100% [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Reading database ... 497049 files and directories currently installed.) [/FONT][/COLOR]
[FONT=Verdana][COLOR=black]Unpacking sacred-gold (from .../sacred-gold_1.0.03-0ubuntu1_amd64.deb) ... [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]dpkg: error processing /var/cache/apt/archives/sacred-gold_1.0.03-0ubuntu1_amd64.deb (--unpack): [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]failed in write on buffer copy for backend dpkg-deb during `./opt/sacred-gold/pak/sound.pak': No space left on device [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]No apport report written because MaxReports is reached already[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Processing triggers for bamfdaemon ... [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Rebuilding /usr/share/applications/bamf.index... [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Processing triggers for desktop-file-utils ... [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Processing triggers for gnome-menus ... [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Processing triggers for hicolor-icon-theme ... [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Errors were encountered while processing: [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]/var/cache/apt/archives/sacred-gold_1.0.03-0ubuntu1_amd64.deb [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Error in function:  [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) [/COLOR][/FONT]
```
 
So knowing that I have TONS of space I ran a quick command to see what was going on 
```

[COLOR=black][FONT=Verdana]xxxx@xxxxxxx:/var/cache/apt/archives$ df -h[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]Filesystem      Size  Used Avail Use% Mounted on[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]/dev/sda1        14G   12G  1.2G  92% /[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]udev            2.0G  4.0K  2.0G   1% /dev[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]tmpfs           784M  884K  783M   1% /run[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]none            5.0M     0  5.0M   0% /run/lock[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]none            2.0G  152K  2.0G   1% /run/shm[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]/dev/sda3       442G   16G  404G   4% /home[/COLOR][/FONT]

```
 
So it appears that it is downloading the file to the sda1 partition which is full. What I need to do, is either move the location of the download from the sda1 partition to the sda3 partition or at least move the install (if temporary held or permanently) to the sda3 partition. 
 
However, i don't know how to do this. The .deb package did download and is currently located in the /var/carche/apt/archives/ folder. I don't know the commands to install from the deb properly. But if someone can give me them, I will move the package and then install.
 
Thank you in advance for your help.
Suspended

---

### Post by suspended on 2012-10-11
Also, I have already run apt-get clean to and that saves the space and the deb package was downloaded when i ran the df command below. 

Not sure what other information could be helpful...

---

### Post by plucky on 2012-10-11
> /dev/sda1        14G   12G  1.2G  92% /

I think you need to investigate why your / partition is so full.

Mine never get above 4G.

Good Luck

---

### Post by Wim Sturkenboom on 2012-10-11
run

```

du -h --max-depth=1

```
That should give you an indication of the space used by the different directories. Next drill down in the largest / larger ones.

/var can have old logfiles that can be deleted
/boot can have old kernels that you no longer need

---

### Post by suspended on 2012-10-11
Thank you, I am at work and won't be able to attempt this until I get home tonight (11 hours or so) but I will start going through things. It does seem quite high and without knowing the inner workings of Linux I am always a bit nervous about cleaning things up. I will respond back with what I find, and other things that I manage to clean up.
 
Thank you again!

---

### Post by suspended on 2012-10-12
So I ran the du command and found that my 2 biggest offenders are the /usr and the /var folder (9G between the 2)
```

6.2G    ./usr
2.8G    ./var

```When I was looking online, it appears that typically the /usr is usually a partition by itself. This doesn't appears to be the case for me. Which would be the most likely cause of my issue. 

[http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html)
> 
 _/usr_   This directory is usually mounted from a separate partition.  It               should  hold  only  sharable,  read-only data, so that it can be               mounted by various machines running Linux.


So any ideas on what the next step would be?

---

### Post by suspended on 2012-10-12
Is there a way I can move the .deb package from the to my home folder and install it from there? And what would the commands be for that?

---

### Post by BrandonIngalls on 2012-10-12
I use a SDD for Ubuntu and I have a 10G root out of the 32G SSD(The extra space is unused)
The way I got around the issue of big files was to move the apt folder to my home partition.

```
sudo mkdir /home/System/
sudo mv /var/cache/apt /home/System/apt/
ln -s /home/System/apt /var/cache/apt
```

This moves the apt folder to your home partition, then creates a symbolic link to that folder in-place of the old one.

---

### Post by Wim Sturkenboom on 2012-10-13
If one game is already 2GB, I can imagine that you start running out of disk space if you have installed a lot of software ;) My total root partition is about 5 GB but I don't install much.

It's not a matter of not having a separate '/usr'. Yes, if you had a separate '/usr', you would probably not have been in trouble now, but if you had allocated more space for the root partition, you would also not be in trouble.

The problem with separate partitions for '/var', '/usr' etc is that you need to decide how big they must be. Choose one too small and you run into problems as well. You might end up with plenty space in '/' but no space in '/usr'. For non-server systems, I would not split too much.

The way forward is
[LIST=1]
[*]make a backup of important data
[*]resize your current home partition to the extra space that you think you need for the root partition (e.g 20GB extra so resize to 20GB)
[*]create a new partition in the free space; this will be your future home partition
[*]mount the future home partition temporarily somewhere (e.g. /mnt/newhome)
[*]copy the content of your current home partition to the mounted future home partition
[*]delete the current home partition
[*]resize the root partition to add the space of the old home partition
[*]tell the system to use the new home partition
[/LIST]

A re-install might be easier, but it can be done as described above (as far as I know; never tried resizing). Personally I do a re-install as I don't trust resizing tools. And I don't trust them as I don't know how they work ;)

---

