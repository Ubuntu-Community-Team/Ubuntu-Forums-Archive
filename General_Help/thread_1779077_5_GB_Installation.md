---
title: "5 GB Installation?"
date: 2011-06-09
forum: General Help
---

### Post by Twux245 on 2011-06-09
[COLOR=Teal][B]Hai durr! I'm in doubt!! Why the heck does ubuntu say I have 27 MB of free space left? I did a 5 GB Installation and I haven't downloaded anything but upgrades and I also have Minecraft...I've installed a few programs for Ubuntu (i.e: Wine, Compiz, RecorditNow, invgrid 0.9)

I use Ubuntu 10.10 and I made a partition and its 50 GB

[SIZE=3][COLOR=Red]**Notice:[/COLOR][/SIZE] I used Wubi.exe to install Ubuntu 10.10

Am I not doing something I should be doing?
[/B][/COLOR]

---

### Post by -kg- on 2011-06-09
> **Twux245 said:**
> [COLOR=Teal][B]Hai durr! I'm in doubt!! Why the heck does ubuntu say I have 27 MB of free space left? I did a 5 GB Installation and I haven't downloaded anything but upgrades and I also have Minecraft...I've installed a few programs for Ubuntu (i.e: Wine, Compiz, RecorditNow, invgrid 0.9)

I use Ubuntu 10.10 and I made a partition and its 50 GB

[SIZE=3][COLOR=Red]**Notice:[/COLOR][/SIZE] I used Wubi.exe to install Ubuntu 10.10

Am I not doing something I should be doing?
[/B][/COLOR]

Need a little more information here.

You created a 50 GB partition?  What for, and what did you format it as?  What is in it?

The reason I ask the above questions is that Wubi installs to a Windows partition.  If you formatted the 50 GB partition as ext(x) (the native format for Linux), Windows will not recognize it and won't install Ubuntu in it.

As far as a 5 GB installation, that's really not nearly enough space for Ubuntu.  I have an old laptop with Lucid (10.04) installed on a 10 GB hard drive, and that's barely sufficient.  Wine can take some space, and I'm not sure about the rest, but you can quickly run out of space with only 5 GB allocated.

Open a terminal and issue the following command:

```
sudo fdisk -l
```

That will show us what you're dealing with.

---

### Post by idoitprone on 2011-06-09
as the guy said above, you used wubi to install. It is in your windows partition right now.

Note: make sure you dont upgrade, you might end up overwriting the windows bootloader before you can make changes. In case you have issues and need to boot windows, you will add another hassle

To uninstall ubuntu
go to control panel and uninstall like any other program

to properly install ubuntu
get a live cd and install ubuntu

btw, what are you going to do about swap. Swap partition or swap file?

---

### Post by Twux245 on 2011-06-09
> **-kg- said:**
> Need a little more information here.

You created a 50 GB partition?  What for, and what did you format it as?  What is in it?

The reason I ask the above questions is that Wubi installs to a Windows partition.  If you formatted the 50 GB partition as ext(x) (the native format for Linux), Windows will not recognize it and won't install Ubuntu in it.

As far as a 5 GB installation, that's really not nearly enough space for Ubuntu.  I have an old laptop with Lucid (10.04) installed on a 10 GB hard drive, and that's barely sufficient.  Wine can take some space, and I'm not sure about the rest, but you can quickly run out of space with only 5 GB allocated.

Open a terminal and issue the following command:

```
sudo fdisk -l
```That will show us what you're dealing with.
[COLOR=Teal]**Ubuntu works fine...I'm just running out of space...well if 5 GB isn't enough to install then why do they even have that option? I installed ubuntu on a 50 GB Hard drive, my hard drive in total is half a TB. (500 GB)**[/COLOR]

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **Twux245 said:**
> [COLOR=Teal]**Ubuntu works fine...I'm just running out of space...well if 5 GB isn't enough to install then why do they even have that option? I installed ubuntu on a 50 GB Hard drive, my hard drive in total is half a TB. (500 GB)**[/COLOR]

You have a half a terrabyte hard drive..  Why don't you just install Ubuntu 10.10 side-by-side with a disc of Ubuntu or a Live Bootable Flash Drive of Ubuntu? The Ubuntu installation will resize your harddrive so you will have half for Windows and Half for Ubuntu or whatever you want.  And it's way faster than Wubi.

Here are some instructions to get started:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by oldfred on 2011-06-09
Wubi is intended for Windows users as an extended test to try Ubuntu. It does not require a partition, but is not intended for heavy duty use.

The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If willing to allocate 50GB then do a full install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

With Natty Manual partitioning is Something Else
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Twux245 on 2011-06-10
> **linuxinstalledfromhdd said:**
> You have a half a terrabyte hard drive..  Why don't you just install Ubuntu 10.10 side-by-side with a disc of Ubuntu or a Live Bootable Flash Drive of Ubuntu? The Ubuntu installation will resize your harddrive so you will have half for Windows and Half for Ubuntu or whatever you want.  And it's way faster than Wubi.

Here are some instructions to get started:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)
**[COLOR=Teal]Now this is useful. Thanks :)[/COLOR]**

---

### Post by Twux245 on 2011-06-10
> **oldfred said:**
> Wubi is intended for Windows users as an extended test to try Ubuntu. It does not require a partition, but is not intended for heavy duty use.

The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If willing to allocate 50GB then do a full install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

With Natty Manual partitioning is Something Else
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[COLOR=Teal]**:D Thanks as well. I'll keep this in mind and I'll do it tomorrow morning :)**[/COLOR]

---

