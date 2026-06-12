---
title: "What's the best way to duplicate a HDD"
date: 2010-05-30
forum: General Help
---

### Post by N.Simpson on 2010-05-30
Long story short, I need several identical systems set up with exactly the same packages and config files. I have one system up and running at present, what is the best way to duplicate the HDD contents to the other systems?

---

### Post by cariboo on 2010-05-30
Have a look at [Clonezilla]("http://clonezilla.org/").

---

### Post by N.Simpson on 2010-05-30
> **cariboo907 said:**
> Have a look at [Clonezilla]("http://clonezilla.org/").

Thanks for the pointer, I'll get on that in the morning.

---

### Post by JustinR on 2010-05-30
If you would like a more graphical approach, you could try Easeus Disk Copy. Both programs (Clonezilla and Disk Copy) both work on the same level, bit by bit copying, and both are free!

[http://www.easeus.com/disk-copy/](http://www.easeus.com/disk-copy/)

---

### Post by dragos240 on 2010-05-30
Open a terminal.
sudo -s
dd if=/dev/??? of=copy_of_hd.img

How to figure out the hard drive device file:
IDE = hdx
SATA = sdx

First IDE hard drive = hda
Second SATA hard drive = sdb

Copy the file somehow, and do:
dd if=copy_of_hd.img of=/dev/???

---

### Post by Nythain on 2010-05-30
> **dragos240 said:**
> Open a terminal.
sudo -s
dd if=/dev/??? of=copy_of_hd.img

How to figure out the hard drive device file:
IDE = hdx
SATA = sdx

First IDE hard drive = hda
Second SATA hard drive = sdb

Copy the file somehow, and do:
dd if=copy_of_hd.img of=/dev/???
+1 for dd :)

---

### Post by handy on 2010-05-30
dd had failed for me, where Clonezilla was successful.

Clonezilla uses dd on certain file systems & also uses other tools for other file systems.

I for one will never use dd on its own again. It wasted an enormous amount of my time.

---

### Post by JustinR on 2010-05-30
> **handy said:**
> dd had failed for me, where Clonezilla was successful.

Clonezilla uses dd on certain file systems & also uses other tools for other file systems.

I for one will never use dd on its own again. It wasted an enormous amount of my time.

I thought DD and Clonezilla both copied things bit by bit?

---

### Post by handy on 2010-05-30
> **JustinR said:**
> I thought DD and Clonezilla both copied things bit by bit?

As I said Clonezilla uses a variety of tools including dd, they are applied relative to the type of file system that needs to be copied, one way or another.

I first used dd to clone a 320GB drive to a 1.5TB drive. The file systems used on the 5 partitions were fat32, HFS+, Ext3, JFS. dd copied the drives but there was no way, & I tried them all, that it would boot the existing Arch system. The partitions were there, but this insurmountable problem existed.

I did the job again this time using Clonezilla, after which everything worked perfectly & has been for many months.

I used dd correctly, I researched that topic well, before the job.

So, apart from the time it took for the cloning process, I spent a long day searching the web in an attempt to find a solution that would work. None was found.

---

### Post by ezsit on 2010-05-30
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Remastersys allows for the easy creation of complete backup to live CD or DVD and re-installation to multiple computers. Dist mode leaves out the /home folder and just preserves the installed programs. 

Backup and Dist mode have their uses, but re-installation on unlimited number of computers with varying hardware and harddrives is no problem since each installation is done with Ubuntu's own installer. Backup mode preserves the user's home and all logins and passwords are retained. Dist mode is best for setting up an Ubuntu computer once and creating installation media to duplicate the initial install.

---

### Post by N.Simpson on 2010-05-31
> **dragos240 said:**
> Open a terminal.
sudo -s
dd if=/dev/??? of=copy_of_hd.img

How to figure out the hard drive device file:
IDE = hdx
SATA = sdx

First IDE hard drive = hda
Second SATA hard drive = sdb

Copy the file somehow, and do:
dd if=copy_of_hd.img of=/dev/???

I know that dd is a possible solution but the problem is that part that says 'Copy the file somehow'. 

I guess I could live boot each system from USB, network mount the disk image and then dd. I guess I'll have to think about how many systems this needs to run on to work out how much time I should invest in setting up a more automated solution.

---

