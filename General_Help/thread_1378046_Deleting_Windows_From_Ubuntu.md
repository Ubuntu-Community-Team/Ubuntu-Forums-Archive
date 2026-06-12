---
title: "Deleting Windows From Ubuntu"
date: 2010-01-10
forum: General Help
---

### Post by joelandsonja on 2010-01-10
Alright, I have searched for this on all of the forums, and I simply cannot find what I am looking for. 

I had to format and reinstall windows and Ubuntu on my system today, but before I throw myself out the window because of frustration I need to ask a few questions. ](*,)

I am trying to uninstall Windows from Ubuntu, but it seems that Windows and Ubuntu are installed on the same drive. (Same Partition)   

I'll include a screenshot at the bottom of the message:

How do I delete windows from my system (EASILY) and use all 320GBs on Ubuntu rather than using only the 17GB that comes with Ubuntu during installation. 

* I'm not sure what kind of information you need, but I am running on Ubuntu 9.10 with Windows XP also installed. (Since I had to install Ubuntu from within Windows)

---

### Post by running_rabbit07 on 2010-01-10
Please attach the pic using the paperclip icon within the posting screen.

[s]Did you install Ubuntu using Wubi?[/s]

You need to install via a LiveCD.

---

### Post by joelandsonja on 2010-01-11
I installed Ubuntu using Wubi, but I also found something interesting when I went to the System Monitor/File Systems ...

I'll include a picture:

As you can see, in the System Monitor/File Systems it is showing a 16.1GB space (Ubuntu), a 298.1GB space (Windows), and a 232.9GB external harddrive that is plugged in. 

Not sure if this helps, but any suggestions would be nice.

---

### Post by running_rabbit07 on 2010-01-11
Ubuntu is currently installed in a virtual partition. There is no way to delete Windows without deleting the virtual partition.

---

### Post by linden940 on 2010-01-11
I'll say reformat the whole thing and make a new partition and go from there.

---

### Post by vinnywright on 2010-01-11
I'd say if your dumping windows and going strate Ubuntu I'd get a Gparted live cd and use that to make 3-4 partitions out of your 320Gig's

1-linux swap 2Gig

2-linux ext3 15 Gig for /root

3-linux ext3 100-200 Gig for /home

4-linux ext3 the rest for storage

then do your install and at the partitioning part click the manual button and next and asine the mount points for / and /home at the sumery page click the advanced button and put grub in sda's MBR

yes you installed thrugh WUBI and it's all inside windows with no way to remove windows and keep Ubuntu

VINNY

---

### Post by mocoloco on 2010-01-11
It can be done!  I did it on my son's computer.  Here's the info. [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

It worked without problems, however I will say I only did it because there was nothing on his system of tremendous value so if it had failed I wouldn't have cared that much.  In other words a backup is always a good idea. Backup your /home folder and you're safe, and if the conversion fails you can just fresh install and load your backed up data.

---

### Post by running_rabbit07 on 2010-01-11
> **vinnywright said:**
> I'd say if your dumping windows and going strate Ubuntu I'd get a Gparted live cd and use that to make 3-4 partitions out of your 320Gig's

1-linux swap 2Gig

2-linux ext3 15 Gig for /root

3-linux ext3 100-200 Gig for /home

4-linux ext3 the rest for storage

The layout is perfect, but I would use EXT4, it is a bit faster. To the OP, I wish you luck and feel free to keep asking questions.

---

### Post by joelandsonja on 2010-01-12
Apparently the last time I burned Ubuntu on a CD I didn't make a proper bootable CD.  So I basically reburned it as a bootable disk, and installed it over everything.  But thanks for the help regardless!

---

