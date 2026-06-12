---
title: "how to partition hard drive for dual boot"
date: 2009-09-04
forum: General Help
---

### Post by hairchin67 on 2009-09-04
i need to have windows for a college class. I want to partition the hard drive so i can have a dual boot capability. I want to use ubuntu as my main os and leave a little percentage for windows to do my college stuff. please tell me how to do this!

---

### Post by imhotep59 on 2009-09-04
I think that windows is already installed on your PC. What version XP or Vista or Seven ?

To partition your hard drive you can use the LiveCD of Ubuntu and use Gparted to have a look at your partitions. Could you tell how is your hard drive partitioned ? I need these inforamtions to help you.

---

### Post by hairchin67 on 2009-09-04
my hard drive is currently not partitioned i wish to divide it like 90% ubuntu and 10% windows

---

### Post by imhotep59 on 2009-09-04
OK, so it's quite simple.

First boot with the liveCD and launch gparted as i previously said.
Then make a first primary bootable partition in NTFS for windows. Up to 40 to 50 Go is enough
Then make a second primary partition in ext3 (or ext4 if you use Jaunty 9.04) for the file system of Ubuntu which will be called / For this partition 10-15 Go will be enough but you can use 20 Go if you really want to install a lot of soft.
Then make an extended partition that you can divide in 2:
- /home in ext3 or ext4 for your data with ubuntu
- one NTFS partition which will be used to exchange datas between windows and ubuntu (because windows cannot read ext partitions, but ubuntu is able to read NTFS)
Don't forget a partition for the swap. It has to be about 1.5 to twice as your RAM
Hope i am clear.

---

### Post by hairchin67 on 2009-09-04
can any one make this simpler for me is there an easier way to partition the hard drive

---

### Post by imhotep59 on 2009-09-04
You have another way to do this. Boot your PC with the live CD and begin to install Ubuntu. This will automatically access to the partitionning tool gparted. However if you never have partitioned a hard drive i can give you a link to help you but it is in french.
[http://doc.ubuntu-fr.org/installation_partitionnement](http://doc.ubuntu-fr.org/installation_partitionnement)

---

### Post by bill516 on 2009-09-04
imhotep has you on the right track.  Follow the link below to a HowTo at the System76 site.  It assumes you have Ubuntu on your machine and that you wish to add Windows.  It is written for System 76 machines, but it applies to any machine that runs Ubuntu, for which a person wishes to add Windows.  Just follow along.

Let me reinforce one point.  Back up your data before you do anything - please!

Here's the link:

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

Formatting looks funny here, but if you copy and paste it will work.

---

### Post by hairchin67 on 2009-09-04
how do i go about backing up my home files before i format my hard drive

---

### Post by imhotep59 on 2009-09-04
I think that bill thought there was something on your drive. If no, you don't have to backup, of course.

---

### Post by hairchin67 on 2009-09-04
> **imhotep59 said:**
> I think that bill thought there was something on your drive. If no, you don't have to backup, of course.

there is all of my files are on ubuntu how do i back them up?

---

### Post by hairchin67 on 2009-09-04
all of my files are on ubuntu now how do i back them up because im only using windows for school

---

### Post by imhotep59 on 2009-09-04
Sorry, i didn't understand !
The most important thing is to backup the datas of your /home by copying them on an external hard drive or a USB key.

---

### Post by bill516 on 2009-09-04
again imhotep is right.  Plug in an external HD or jump-drive and copying your Home directory is a simple drag 'n drop operation.  Just make sure the external device is formatted in such a way that you can work with it easily.  Given that you are installing Windows I would choose Fat32 or NTFS.  Windows and Ubuntu will both read those.

Main thing:  Get in the backup habit.  You cannot afford the risk of losing vitally important work because your HD takes a holiday.

---

### Post by imhotep59 on 2009-09-05
Thank you, Bill.
If you have files greater than 4 Go to backup, you will have to format your external HD in NTFS because FAT32 cannot support such big files.

---

