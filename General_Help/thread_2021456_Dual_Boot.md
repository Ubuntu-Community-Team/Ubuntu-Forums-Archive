---
title: "Dual Boot"
date: 2012-07-09
forum: General Help
---

### Post by Alphalogan on 2012-07-09
After a break of several years I wish to return to Ubuntu but need some advice. I want to be able to use W7 - 64 bit for certain programmes and Ubuntu for my main useage including internet and e-mail. The reason for this I do a lot of video editing using Sony Vegas in W7 which is not only power hungary but also memory hungary, it has also taken me some time to get used to it so I have no wish to use any other programme. When I had Ubuntu before I was able to dual boot into either Ubuntu or Windows when starting, is this still the best way and if so where can I find instructions how to do>
Many thanks

---

### Post by oldfred on 2012-07-09
If you have a lot of RAM which you should for Video editing and have a newer computer, you will want the 64 bit version. You then need to burn a CD, although I now prefer to use USB flash drives to install.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If installing on the same drive, use Windows to shrink the Windows partition. Also how many partitions are used? Many default Windows installs use all 4 primary partitions, so you have to decide how to repartition.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Install:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Several other sites with screen shots of installing process. Installer has not changed much so different versions are still relevant.

Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


Of course many just jump in and install. If you do not have the 4 partition limit it will automatically work creating the default of / (root) and swap. But I prefer to manually partition, to add extra partitions for shared data (NTFS) or /home but do not know you drive size or experience with partitioning.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by GreatDanton on 2012-07-09
Hi, and welcome to the forums. Yes this option is still possible. You can either boot from CD or live USB, and then use Gparted to shrink Windows7 partitions. WARNING: Before you do that make sure you made backups. After you shrink Windows7 with Gparted, just run Ubuntu Installer (select something else instead of full install) and Ubuntu will take care of all other things.

I hope someone of Ubuntu staff will tell you more about this topic.

Good Luck!

EDIT: ooops, oldfred was faster ;)

---

### Post by Alphalogan on 2012-07-09
Many thanks - I'm on my way!

---

### Post by Mark Phelps on 2012-07-10
Do NOT use GParted to shrink win7 --doing so is asking for trouble as that can lead to filesystem corruption, rendering Win7 unbootable afterward.

Instead, use ONLY the Win7 Data Management utility to shrink Win7.  That is not as flexible as GParted, but it will not result in any filesystem corruption.

---

### Post by Hydera5 on 2012-07-10
Thank you, you just saved me a lot of trouble!

---

