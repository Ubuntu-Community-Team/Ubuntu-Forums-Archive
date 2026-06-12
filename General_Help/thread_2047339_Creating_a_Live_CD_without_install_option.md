---
title: "Creating a Live CD without install option"
date: 2012-08-24
forum: General Help
---

### Post by xitronznz on 2012-08-24
What I'm trying to accomplish is to create a LiveCD based on Ubuntu 12.04 Desktop that has pre-configured apps on it for a very limited user base.  Primarily a VPN for them to access the work network from home, with IP address and domain already programmed into it, and with Firefox and Chrome set up with 3 home tabs that will automatically open so the user can easily access our internal web servers.  I've created the source by doing a VirtualBox install of Ubuntu 12.04 Desktop and customizing it as required.

What I do *not* want is for them to have the ability to accidentally select "Install Ubuntu" and wipe their hard drives, either from the boot up or from the desktop.

The only suggestion I've found for same involves using remastersys, but first editing the script to comment out every line that refers to ubiquity.  I began that process, and believe that doing so would cripple the script.

Can anyone point me to a URL that describes how to create a Live CD that allows a person to boot into their computer, but without adding on the option of installing the OS., and which allows this disk to be created based on a pre-existing installation of Ubuntu 12.04, like you could do with remastersys?

Thank you very much!

Xitron / Benny

---

### Post by Cheesehead on 2012-08-24
[http://live.debian.net](http://live.debian.net)
It's not a set of instructions. Debian Live is the actual build tool. There's even an online build tool.

1) Tell it you want Ubuntu 12.04
2) Add your list of packages
3) Add your specialty config files

---

### Post by xitronznz on 2012-08-27
Man, oh man, do I hate to sound stupid, but...

I'm absolutely uncertain what to do with that page.  It has the following links:

        [User]("http://live.debian.net/user")      
[LIST]
[*][Archive]("http://live.debian.net/archive")
[*]**Download releases:** [stable]("http://cdimage.debian.org/cdimage/release/current-live/") [oldstable]("http://cdimage.debian.org/cdimage/archive/5.0.10-live/")
[*]**Download snapshots:** [daily]("http://live.debian.net/cdimage/daily-builds") [weekly]("http://live.debian.net/cdimage/weekly-builds") [monthly]("http://live.debian.net/cdimage/monthly-builds")
[*][About release images]("http://www.debian.org/CD/live/")
[*]**Manual**: [stable]("http://live.debian.net/manual-2.x/html/") [unstable]("http://live.debian.net/manual-3.x") [oldstable]("http://live.debian.net/manual-1.x")
[*][Mailinglist]("http://lists.debian.org/debian-live/")
[*][**Web Images Builder**]("http://live-build.debian.net/")
[/LIST]
 
       [Development]("http://live.debian.net/devel")      
[LIST]
[*][live-boot]("http://live.debian.net/devel/live-boot/")
[*][live-build]("http://live.debian.net/devel/live-build/")
[*][live-config]("http://live.debian.net/devel/live-config/")
[*][live-debconfig]("http://live.debian.net/devel/live-debconfig/")
[*][live-installer]("http://live.debian.net/devel/live-installer/")
[*][live-manual]("http://live.debian.net/devel/live-manual/")
[*][live-tools]("http://live.debian.net/devel/live-tools/")
[*][other]("http://live.debian.net/devel/other/")
[*][RFC]("http://live.debian.net/devel/rfc/")
[/LIST]
 
       [Project]("http://live.debian.net/project")      
[LIST]
[*][About]("http://live.debian.net/project/about")
[*][Contact]("http://live.debian.net/project/contact")
[*][Deployment]("http://live.debian.net/project/deployment")
[*][Downstream]("http://live.debian.net/project/downstream")
[*][Lifespan]("http://live.debian.net/project/lifespan")
[*][Links]("http://live.debian.net/project/links")
[*][News]("http://live.debian.net/project/news")
[*][Releases]("http://live.debian.net/project/releases")
[*][Roadmap]("http://live.debian.net/project/roadmap")
[*][Status]("http://live.debian.net/project/status")
[*][Team]("http://live.debian.net/project/team")
[/LIST]
 
  
  
I've no idea which I'm supposed to grab, nor what I'm supposed to do with them.  The manual is more of a step by step process, which differs from what you said, so I'm guessing that I'm just not looking at the page right.  Any clues?

Benny / Xitron

---

### Post by xitronznz on 2012-09-14
For anyone else fighting this battle, I've managed to accomplish the mission.  I installed Ubuntu 12.04 Desktop i386 non-pae to VirtualBox, did my changes for the end user, then used remastersys to build an iso.  I then brought the resulting iso file to my Ubuntu workstation, used the instructions from: 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
...to extract the CD, shrink it still further, and edited the isolinux.cfg file to remove all but the LiveCD option from the menu.  I also had to remove the ubiquity icon from the user's Desktop folder.

Benny / Xitron

---

### Post by Primefalcon on 2012-09-14
> **xitronznz said:**
> For anyone else fighting this battle, I've managed to accomplish the mission.  I installed Ubuntu 12.04 Desktop i386 non-pae to VirtualBox, did my changes for the end user, then used remastersys to build an iso.  I then brought the resulting iso file to my Ubuntu workstation, used the instructions from: 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
...to extract the CD, shrink it still further, and edited the isolinux.cfg file to remove all but the LiveCD option from the menu.  I also had to remove the ubiquity icon from the user's Desktop folder.

Benny / Xitron
Thx for the update.... This will be useful to me in the future :D

---

### Post by black veils on 2012-09-14
maybe its possible to add a boot parameter to bypass the menu, and then uninstall ubiquity. as a simpler alternative.

---

### Post by VeTRooTdub on 2012-09-14
It does not approach me. Perhaps there are still variants?
 
 
Up D 
I apologize for flooding, just curious tools 

[Spy Software for Mobiles](http://mobilespy.servicesfrom.com) - Control your employees' phone costs. Read SMS, call logs for only $0.

---

