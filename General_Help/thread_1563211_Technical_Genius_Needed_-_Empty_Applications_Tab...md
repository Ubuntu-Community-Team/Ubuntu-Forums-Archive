---
title: "Technical Genius Needed - Empty Applications Tab...Please help"
date: 2010-08-28
forum: General Help
---

### Post by DavidOfLondon on 2010-08-28
Hi guys,

I recently had my first "You're Not in Kansas Any more" moment when I tried to install the menus from BackTrack to run on Ubuntu 10.04 (I was thinking of adding some of the security tools) and the instructions I followed didn't save a backup of my menu settings, even though it said it would.

In** usr/share/applications** I can see all my apps that I use sitting there but without the original tabs under Applications [COLOR=SeaGreen][COLOR=Blue]**how am I supposed to add them all back?! Plus, to make matters worse, the Ubuntu Software Centre is not in that folder !**[/COLOR]
[/COLOR] 
I followed all the steps from this site in order to destroy my settings: 

[http://micksmix.wordpress.com/2009/11/20/getting-the-backtrack-menu-structure-and-tools-in-ubuntu/#PrepareMenu-](http://micksmix.wordpress.com/2009/11/20/getting-the-backtrack-menu-structure-and-tools-in-ubuntu/#PrepareMenu-)

The net result is my Applications tab is empty now and I therefore have nothing in and can't locate any apps without exceptional tedium. All functionality in Edit Menus is gone - if I try to add a new menu/item it won't let me rename it or add an icon or anything. Clearly I've deleted or disabled the files or folders controlling this panel and it's driving me crazy. For all the talk of Ubuntu's "user friendly" style I have to say in windows this would take seconds to mend instead of having to scan the internet endlessly.

_[COLOR=Blue]**How do I repopulate the Applications bar so that it picks everything up and at least makes the main original settings reappear?**[/COLOR]_

**[COLOR=Blue]When I right click to Edit Menus the items section is empty[/COLOR]**. I've reinstalled the various Gnome apps, restarted, enterred all kinds of terminal commands....nothing.

Surely there is an override for this without having to reinstall my entire life??

I just cannot find a solution anywhere and don't want to have to reinstall just because of a menu.

Ubuntu Software Centre is also gone from the Applications tab. If I click on the Applications tab NOTHING happens. Zero.

Please help.

Thanks,

David.

My last attempt at something was this:

david@david-laptop:~$ sudo apt-get install menu-xdg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  menu-xdg
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 5,170B of archives.
After this operation, 77.8kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe menu-xdg 0.5 [5,170B]
Fetched 5,170B in 0s (33.8kB/s)   
Selecting previously deselected package menu-xdg.
(Reading database ... 155844 files and directories currently installed.)
Unpacking menu-xdg (from .../archives/menu-xdg_0.5_all.deb) ...
Processing triggers for menu ...
Setting up menu-xdg (0.5) ...

Processing triggers for menu ...
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
david@david-laptop:~$ apt-get
apt 0.7.25.3ubuntu9.1 for i386 compiled on Jul 16 2010 08:12:08
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

---

### Post by Pollox on 2010-08-29
I believe deleting the .gnome2 folder in your home directory should set your Applications menu back to default.  You might have to log out for the change to take effect.  Definitely be sure to backup your .gnome2 folder before deleting, so that if you are displeased with the results (it will reset a lot of settings), you can just undo it.

---

