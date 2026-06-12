---
title: "Trying To Uninstall Ubuntu"
date: 2011-12-15
forum: General Help
---

### Post by adamantasaurus on 2011-12-15
Hello All,

This is my first post on this forum and my third day using ubuntu. Well I am trying to use it to setup a web server and initially installed it on my old laptop, but I want to put it on the desktop I am currently on right now. 

I insert the win xp cd I have into my laptop and get to the part where it says select the partition that you wish to put winxp on but there is no partition to choose from. So I hit enter anyway and it tells me windows is shutting down to prevent damage to your computer. 

Do I have to reformat ubuntu as an NTSF? If so How do I do that?

Any help would be greatly appreciated and thank you in advance.

---

### Post by TBABill on 2011-12-15
If you fire up your Ubuntu liveCD you can go into gparted and mount the hard drive, then partition and format it to whatever you want, then restart and install WinXP to the entire drive.

---

### Post by adamantasaurus on 2011-12-15
I have the Ubuntu Server CD I put that in and nothing happens it just gives me ETCD and a copywright with some guys Name. 

Do I have to download the ubuntu desktop version put it on a cd and boot that?

---

### Post by astrognome on 2011-12-15
Here is a great step-by-step guide to the server version of ubuntu.  This has everything in it needed to install and customize your server to your liking.

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Let me ask you, do you want your desktop to be a dual boot, or solely to act as a server?

---

### Post by spielball on 2011-12-15
You can download the ISO of the GParted Live CD and burn it to a CD. Then start from that CD. It will boot into a basic Linux which provides GParted for managing your partitions. Then just delete the Linux partitions of your hard drive and create new partitions in NTFS format.

Link:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by seawolf167 on 2011-12-15
Uninstalling Ubuntu:

Simply erase the existing partitioning scheme through the Windows installer when prompted where to install to, then create a new [blank] partition which Windows will then install too.


Installing Ubuntu:

To start with - the Ubuntu Server version does not come with a GUI installed for a number of reasons, so if you are unfamiliar with, or not 
very good at using the terminal interface, you can use the desktop version instead. There are pros and cons to each, but if this is simply for a do-it-yourself home webserver you'll be just fine with the desktop version.

You don't need to partition anything before-hand, the installer can do that for you. You can simply have it setup the partitions and sizes automatically for you. There are a number of ways you can improve upon the automatic partitioning scheme, and if you are interested ask away. Some reading on partitioning schemes can be [found here]("https://help.ubuntu.com/community/PartitioningSchemes").

As for actual installation, there is a desktop installation [guide here]("https://help.ubuntu.com/community/Installation") if you are unfamiliar with installing Ubuntu.

Once you get Ubuntu up and running, the most common way to run a webserver is by using Apache2, a guide for setting up and running that is [located here]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html"). Note that this guide is in the "server guide" section, so it assumes you do not have a GUI installed. Additionally, there are probably quite literally tens of thousands of tutorials scattered across the internet, most of which are a google search away.

As mentioned before, please feel free to ask away with any questions you may have or issues you may run into!

---

### Post by adamantasaurus on 2011-12-15
> **astrognome said:**
> Here is a great step-by-step guide to the server version of ubuntu.  This has everything in it needed to install and customize your server to your liking.

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Let me ask you, do you want your desktop to be a dual boot, or solely to act as a server?

Yea I think I want to use it just as a server, is that a bad idea?

---

### Post by adamantasaurus on 2011-12-15
Thank you All for all the useful information that you have provided me very helpful thank you.

---

### Post by adamantasaurus on 2011-12-15
> **spielball said:**
> You can download the ISO of the GParted Live CD and burn it to a CD. Then start from that CD. It will boot into a basic Linux which provides GParted for managing your partitions. Then just delete the Linux partitions of your hard drive and create new partitions in NTFS format.

Link:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Thank You I will definitely try that and let you know what happens.

does this guide cover setting up apache mysql and php5 also?

Thanks

---

### Post by adamantasaurus on 2011-12-15
........

---

### Post by adamantasaurus on 2011-12-15
..........

---

### Post by seawolf167 on 2011-12-15
Here are the 10.04 server guides you were looking for

[ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[HTTPD - Apache2]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html")
[PHP5]("https://help.ubuntu.com/10.04/serverguide/C/php5.html")
[MySQL]("https://help.ubuntu.com/10.04/serverguide/C/mysql.html")

---

### Post by adamantasaurus on 2011-12-15
> **spielball said:**
> You can download the ISO of the GParted Live CD and burn it to a CD. Then start from that CD. It will boot into a basic Linux which provides GParted for managing your partitions. Then just delete the Linux partitions of your hard drive and create new partitions in NTFS format.

Link:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Idk if I did this right but it didn't work. 

What I did is this I put the cd in my drive and let it boot up on it's own and it brought me to a UI of a desktop type area where I saw all three of my partitions. I deleted 2 of the them (it wouldn't let me delete the other one). I put my windows cd back in after that and it still didn't recognize that I had any partitions. 

Am I doing this wrong?

---

### Post by spielball on 2011-12-16
> **adamantasaurus said:**
> Idk if I did this right but it didn't work. 

What I did is this I put the cd in my drive and let it boot up on it's own and it brought me to a UI of a desktop type area where I saw all three of my partitions. I deleted 2 of the them (it wouldn't let me delete the other one). I put my windows cd back in after that and it still didn't recognize that I had any partitions. 

Am I doing this wrong?

Usually, there shouldn't be any problem to edit or delete a partition with GParted. But perhaps you first need to delete the 'inner' partition, then the 'outer' one. That means, your third partition is perhaps a logical partition ('inner') which is embedded in an extended partition ('outer'). So you need to delete the logical partition first. Also make sure the partition is not mounted:

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-unmount-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-unmount-partition)

If you don't want to install XP on that laptop, but an Ubuntu Server  environment, then you can just use a normal Ubuntu Live CD, boot from  that CD, and then create/delete/format partitions with the built-in hard  disk manager.

But as far as I understood, you want to install XP on this laptop? If it's a new laptop, it will most likely have a SATA hard disk. But Windows XP is a vintage OS and doesn't support SATA hard disks by default, which means the Windows XP install cd doesn't provide the needed drivers, thus cannot 'see' the hard disk.

If that is the case, then you need to go to your laptop's BIOS (usually by pressing some key like F2 when it boots up -- the shortcut depends on your laptop/BIOS and will be displayed when you start the laptop). Then, in the BIOS settings, you need to switch off the AHCI mode (or change it to IDE mode if that option is available), then 'Exit and Save Changes' and reboot. Windows XP should now be able to 'see' the hard disk.

You can also install Windows XP in AHCI mode if you provide the needed SATA drivers during the installation routine by pressing F6. However, if you want provide the drivers from an USB stick, you need to have a Windows XP install disk with Service Pack 3. Windows XP up to SP2 can only access floppy drives during install.

Or you can make a customized Windows XP SP3 disk by slipstreaming the AHCI/SATA drivers into the ISO and then burn it. It can be done very simply be using the freeware nLite and slipstreaming a AHCI/SATA driver pack. A driver pack with almost all drivers for various hard disks can be found here:

[http://driverpacks.net/driverpacks/windows/xp/x86/mass-storage/10.09](http://driverpacks.net/driverpacks/windows/xp/x86/mass-storage/10.09)

I hope this helps.

---

### Post by adamantasaurus on 2011-12-16
Thank you ALL for the help, I found a windows vista cd and I tried using that and it worked I just got it installed on there thanks so much.

---

### Post by seawolf167 on 2011-12-16
> **adamantasaurus said:**
> Thank you ALL for the help, I found a windows vista cd and I tried using that and it worked I just got it installed on there thanks so much.

If you have everything solved that you wanted to achieve, please mark this thread as Solved under Thread Tools :)

---

