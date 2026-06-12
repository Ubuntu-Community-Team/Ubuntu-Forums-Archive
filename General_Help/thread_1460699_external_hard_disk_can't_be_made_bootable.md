---
title: "external hard disk can't be made bootable"
date: 2010-04-23
forum: General Help
---

### Post by ppb7 on 2010-04-23
my old pc died not long ago so I retrieved its hard disk and bought a USB enclosure. that HD had a ubuntu 9.04 partition and an XP one.
Something must have gone wrong somewhere as, although i could still boot from jaunty, I was not allowed to upgrade.
It therefore seemed to me natural perform a clean install, so here's what I did:
- on a win7 computer, I inserted a 9.10 bootable disk
- with usb-disk creator, I wanted to install via a spare image so re-formatted the HD
- I couldn't install a mythbuntu 9.10 after that as I giot an error message ("can't mount the drive" or something similar). yet, in win7 the HD is recognised.
 
So, what am I doing wrong?:?: Are USB HDs not included as USB devices that you can make bootable?:?::?:
Or should I be installing a !straight" ubuntu version, then install MythTV?
Thanks in advance for your help,
 
Philippe

---

### Post by klemes on 2010-04-23
So exactly what is your problem now.That you cannot make the let's call it 'A' drive bootable or that you cannot mount lets call it' B' drive in order to install there?
Which one from the above is it?
If it's the first one may I suggest a very comprehensive site with lot's of utilities for making an external HDDrive bootable and that is [www.pendrivelinux.org]("http://www.pendrivelinux.org").**BIG EDIT:It's [www.pendrivelinux.com]("http://www.pendrivelinux.com") not .org.Sorry**.:)
If it's B  I have no clue,but if I understand correctly you are using Windows to make the installation which I don't think it's the best practice and  I really have no experience there 'cause I nevered cared to try this method of installing(wubi I suppose it's called).Better boot off of a LiveCD and proceed with the installation to your external USB hard disk drive directly as if it was an ordinary installation.Could you do that?

---

### Post by ppb7 on 2010-04-23
> **klemes said:**
> Better boot off of a LiveCD and proceed with the installation to your external USB hard disk drive directly as if it was an ordinary installation.Could you do that?
 I think I deid that afew days ago and was not able to partition anything else but the main HDD (which I should not, under penalty of death, touch). But that was before I re-formatted the drive so I will give it another go.
 
> So exactly what is your problem now.That you cannot make the let's call it 'A' drive bootable or that you cannot mount lets call it' B' drive in order to install there?
Which one from the above is it?
If it's the first one may I suggest a very comprehensive site with lot's of utilities for making an external HDDrive bootable and that is [www.pendrivelinux.org]("http://www.pendrivelinux.org/").
If it's B I have no clue,but if I understand correctly you are using Windows to make the installation which I don't think it's the best practice and I really have no experience there 'cause I nevered cared to try this method of installing(wubi I suppose it's called).
Both I guess; I cannot make it bootable because, after I have re-formatted the drive, I am now told that it can't be mounted. However, I realise that I must not have been clear enough
first, i booted off a live CD, then used the system's usb disk creator program, re-formatted the HDD as required. I may be wrong but a few days ago I was told by the system that I could not install from the liveCD, but, as explained, I'll try again now the disk is blank.

---

### Post by oldfred on 2010-04-23
I am not sure you are doing it correctly. The usb creator is for USB keys to make (copy) the CD to a USB key that you then can use to install on a system either a backup way to install or for a computer that does not have a CD.

I think you just want to to a regular install but want to select sdb to install. With external drives you do have to select the advanced button at the end of the partitioning screens to make sure it installs grub to sdb. It usually installs to sda but then you cannot boot without the external plugged in.

---

### Post by ppb7 on 2010-04-28
> **oldfred said:**
> I think you just want to to a regular install but want to select sdb to install. With external drives you do have to select the advanced button at the end of the partitioning screens to make sure it installs grub to sdb.

Quite right, so here's what I did:
- from the live CD i clicked on install 9.10
- when presented with choices as to how to partition, I chose manual partitioning...:?:
And I am stuck. Manual partitioning is an advanced method for experienced users(which I am not).:(
I have found several Internet pages where there are explanations, but while they always start as if they meant to explain things to beginners, there comes a point when the talk becomes too technical for me. I would therefore be very grateful if you could read those pages and if need be come up wtih an alternative and more newbie-friendly description of how to partition manually a disk.
Remember that the only reason I wish to install jaunty manually is because it is to be a linux-only install meant go on an additional hard drive
The pages are:
[http://ubuntuforums.org/showthread.php?&t=282018]("http://ubuntuforums.org/showthread.php?&t=282018")
[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System]("http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System")
[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html]("http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html").
And what about
[http://linuxplanet.com/linuxplanet/tutorials/3174/1/]("http://linuxplanet.com/linuxplanet/tutorials/3174/1/")?
Could anything useful be gleaned from that?
Thanks in advance for your answers!

Philippe

---

### Post by oldfred on 2010-04-28
Most of the links are using command line to partition, I have not done that since fdisk in DOS days. Just use gparted withc is on the liveCD. Boot the liveCD and do not do the install but run Ubuntu. gparted is under system, administration.

You do need to know about partitions, the standard MBR disk partitions which has been in use since the orginal IBM PC has 4 primary partitions. When they realized that was not enough they allowed one primary to become an extended or holder for additional logical partitions. Windows has to be in a primary but linux does not. Some BIOS need a boot flag on a primary (assumes windows) to even let you boot. So you never want to create more than 3 primary so you can still have an extended partition.

You need plan you partition needs. Minimum are / (root) and swap. I ran my system with just root & swap on one drive and windows and a d: (sda2) NTFS partition to share data with Ubuntu & XP for several years. Many recommend a separate /home and others add additional /data directories. If just starting out you do not have a good idea of sizes so I would just create a 10-20GB root, swap equal to RAM, and the rest as /home. If you have lots of space you can leave some unallocated and use it later.

You can put labels on your partitions but they are just labels. When manually installing you have to select a partition and choose / so it knows that that partition is root. You also select format ext3 or ext4 (or many other choices, but not any windows types). If you have an existing /home you do not format it. It seems to find swap on its own.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

she still uses FAT but I would recommend NTFS if sharing with windows.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

