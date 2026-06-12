---
title: "Partitioning disk space and Ubuntu 10.10 install requirements"
date: 2011-04-13
forum: General Help
---

### Post by dareys on 2011-04-13
Greetings,

I am testing release 10.10 of Ubuntu desktop from a USB boot drive. It looks great so far, and I am thinking of installing it on the machine. However, I would like to know the disk space requirements. I know I could look them up, but this would help. 

Also, while working with the interface I accessed all of the machine´s devices from the Linux OS and saw that I could partition an existing partition. However, that houses the Windows XP SP3 installation and I was wondering if altering partition size would wipe its contents. 

I would be awsome if I could dynamically alter the partition to the size required by Ubuntu plus some slack for applications and the like so I could have both OSs on the same machine without having to reformat the drive for dual boot and re-install both OSs.

Thank you.

Jean-Pierre

---

### Post by earthpigg on 2011-04-13
0) back up vital data

1) people usually advise starting off by running defrag a couple times.

2) I'd use windows tools to shrink the windows partition before starting the ubuntu install. partitioning windows using linux tools can sometimes mean you have to use the windows system restore disk to make windows work again. unless the power goes out or similar, this should not damage or erase any data. if it does, good thing you did step 0.

3) the official minimum requirements, i think, are 4gb. that is crap. allocate at least 10-15 gb. more if you plan to game or put your music/movie collection on the ubuntu partition.

---

### Post by techunit on 2011-04-13
You should be fine Ubuntu needs about 4GBs I'd give it at least 10GBs. You can just shrink the windows XP partition without worry. Have fun and good luck.

---

### Post by dareys on 2011-04-15
> **earthpigg said:**
> 0) back up vital data

1) people usually advise starting off by running defrag a couple times.

2) I'd use windows tools to shrink the windows partition before starting the ubuntu install. partitioning windows using linux tools can sometimes mean you have to use the windows system restore disk to make windows work again. unless the power goes out or similar, this should not damage or erase any data. if it does, good thing you did step 0.

3) the official minimum requirements, i think, are 4gb. that is crap. allocate at least 10-15 gb. more if you plan to game or put your music/movie collection on the ubuntu partition.
Thank you for the responses! Ok, I will allocate a good 20GB to Ubuntu. 

Related questions.

1. Apparently you can dynamically resize a Windows partition with the OS and data on it without
    destroying anything. If so, what Windows tool do you use to accomplish this non destructive
    resize?

2. The install of UBUNTU I am contemplating would be on a new partition created from the space
     reclaimed from resizing an existing Windows partition with the OS and data on it. Does this sound
     coherent?

Your knowledgeable replies are appreciated as I don´t want to blow away my Windows instalation
just yet.

Thank you.

Jean-Pierre

---

### Post by dareys on 2011-04-15
> **techunit said:**
> You should be fine Ubuntu needs about 4GBs I'd give it at least 10GBs. You can just shrink the windows XP partition without worry. Have fun and good luck.
Shrink Windows partitions dynamically without harm? Sounds too good to be true. I have struggled with just such type of problem on Database file systems and truly, not obvious. If you are right, well, I would have to read about it. What utility would you use to do the re-sizing. Thank you. Jean-Pierre

---

### Post by oldfred on 2011-04-15
With Vista & 7 it is best to use the windows tools to shrink the windows partition sizes. With XP windows does not have any tools, so you can use gparted. I suggest defragging as then you can shrink it faster, but not absolutely required. While data loss is rare, you always want to have good backups. Even the best of us accidentally hit some key and cause all sorts of grief. Or there is a power failure or who knows what can go wrong often does.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by earthpigg on 2011-04-16
> **dareys said:**
> 
1. Apparently you can dynamically resize a Windows partition with the OS and data on it without
    destroying anything. If so, what Windows tool do you use to accomplish this non destructive
    resize?

2. The install of UBUNTU I am contemplating would be on a new partition created from the space
     reclaimed from resizing an existing Windows partition with the OS and data on it. Does this sound
     coherent?

1) Yes, that is true on Ubuntu too. The only caution is that it is often quite time consuming - especially for nearly full partitions. If not for how vastly time consuming to install/configure windows, I'd be suggesting that you simply delete all partitions and create new ones in the sizes you want and then reinstall Windows along with ubuntu - deleting and re-creating partitions is lighting quick, unlike resizing, and installing/configuring most Linux distributions takes about 45 minutes. I understand, though, that it takes a dozen hours to configure windows and thus people value particular windows installations. 

As to what windows tool used to do this? No one knows Windows better than Microsoft, so [I'd go with their advice]("http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk"). :)

2) Yes, Correct.

---

### Post by dareys on 2011-04-19
> **earthpigg said:**
> 1) Yes, that is true on Ubuntu too. The only caution is that it is often quite time consuming - especially for nearly full partitions. If not for how vastly time consuming to install/configure windows, I'd be suggesting that you simply delete all partitions and create new ones in the sizes you want and then reinstall Windows along with ubuntu - deleting and re-creating partitions is lighting quick, unlike resizing, and installing/configuring most Linux distributions takes about 45 minutes. I understand, though, that it takes a dozen hours to configure windows and thus people value particular windows installations. 

As to what windows tool used to do this? No one knows Windows better than Microsoft, so [I'd go with their advice]("http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk"). :)

2) Yes, Correct.
OldFred,

Many thanks for the response. I will dowload gparted and the related documentation carefully, backup and proceed. It is likely to take some weeks so I will let you know how it went after the fact. And yes, of course, I will backup first.

Regards,

Jean-Pierre

---

