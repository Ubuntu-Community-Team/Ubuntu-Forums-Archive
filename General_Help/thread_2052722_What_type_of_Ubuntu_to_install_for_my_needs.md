---
title: "What type of Ubuntu to install for my needs?"
date: 2012-09-03
forum: General Help
---

### Post by chriswt on 2012-09-03
I need someone who really knows what they are doing! 
This is my dilemma. I will make it shot as I can.
My past programming experience is mostly in Microsoft products and some UNIX about 11 years ago.

 Today I wish to learn Ubuntu Linux, Apache, PHP and MySQL to run a SERVER for the Web. Most importantly for now, I want to learn 

Hardware I have is a new HP Pavilion p6-2117c Desktop PC running Windows 7 for my learning.
Two weeks ago, I went to download Linux. Wow &#8211; all the types and versions, shocking.I went with Ubuntu Server 12.04 and installed it with LAMP so I would have PHP, MySQL and Apache installed and configured.

As you may know, I had no DVD or Internet or Web Browser. Also, the monitor will turn off after 10 minutes if I didn&#8217;t press any key or the power saver on the video card, I assume, would turn off and would not go back on. I would then have to type blindly save my vim file and shutdown now.  My refreshing of some commands did come back and I learned stuff by going through the process.

Currently, I had to reinstall Windows 7 from the backup image that I made before installing Ubuntu 12.04. This was done because I went back to try to install more services with the install boot disk and during the install it told me that some services are already install and I could not figure out how the heck to say overwrite or skip or exit or anything else. Therefore I crashed the system and loaded Windows 7.

I&#8217;m thinking that I can reinstall Ubuntu 12.04 Server again since Windows formatted the HD and all Ubuntu will be gone and select All Services during install hoping I&#8217;ll have Firefox, or some type of Web Browser, so I can open my text file when I&#8217;m learning MySQL and PHP.
Install Ubuntu 12.x Desktop version and perhaps the DVD and Internet will work so I can function!!! Will I still be able to learn MySQL, Apache and Ubuntu Linux commands from the prompt? Will THIS HELP ME?
What is you advice?
Thanks

---

### Post by oldfred on 2012-09-03
I am not a server person, so they may have different advice. Many with servers install a minimal gui  like Openbox just to have more than just the command line.

But the underlying kernel is the same regardless of version installed. It just is which gui you have (or none). 

You almost always can repair Ubuntu from either inside or from a liveCD, but server and alternate installers are not liveCDs. You should have a liveCD or repair Disk (Windows) for the current version of every operating system you have installed.

You may want to make the image of Windows after resizing.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
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

Some go all they way back to minimal install which is just a kernel & enough drivers to get on Internet so you can only download those applications you really want. 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you do not like Unity, use K/L/X ubuntu or the DE/ WM of your choice. 
Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)
What is the difference between Debian, Fluxbox, XFCE,
window managers like Icewm, Openbox, Fluxbox, and Xfwm
desktop environments are KDE, Gnome, Xfce, Enlightenment, and LXDE

I am using on my desktop full Ubuntu 12.04 with gnome-panel not Unity. That gives me the older style menus.
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

I would shrink Windows, make good image backup, install Desktop version, decide on one desktop environment & Windows manager. And install all the server components so you can learn how to use those. It took me a longer time to learn Linux commands. I had used CP/M, DOS, but not any Unix nor LInux before.

How much space are you allocating to Windows and Ubuntu. I prefer to have each on their own drive with Windows system partition still smaller and a shared NTFS partition for any data I might want in both systems.

---

### Post by SeijiSensei on 2012-09-04
Install the Windows version of [VirtualBox]("https://www.virtualbox.org/wiki/Downloads") then create a new virtual machine and install Ubuntu Server 12.04 into the VM.  You then have both a server and a client on the same machine.

---

### Post by Cheesemill on 2012-09-04
If this is just for learning then you can use the standard desktop version of Ubuntu.

Any of the packages that are available for the server version (Apache, MySQL and PHP) can also be installed on the regular desktop version as well.

---

### Post by LiamOS on 2012-09-04
Does your box have an ethernet connection? If so, you should be able to have net access straight away on a very minimal install. Use this to install something like openbox and then firefox, to get your graphical environment up and running. It'll be basic, but functional, and you can learn easily in that kind of environment without it having too much overhead.

---

