---
title: "Lucid Lynx upgrade"
date: 2010-06-08
forum: General Help
---

### Post by retiree on 2010-06-08
I just did an upgrade from Hardy Heron to Lucid Lynx and everything runs good except for an error that says "Flashplugin-nonfree. Package is in a very bad inconsistent state- you should reinstall it before attempting a removal. Also flash does still work but very slow to load. Firefox is slower than my Hardy install. What is a solution to this? Running 64 bit on both Hardy and now Lucid Lynx, Thanks

---

### Post by Cypher2 on 2010-06-08
you can open a terminal window and run:

"sudo killall firefox
sudo aptitude purge -y flashplugin-nonfree && sudo aptitude install -y flashplugin installer"

when that finishes run:

"sudo aptitude clean"

---

### Post by lovinglinux on 2010-06-08
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by retiree on 2010-06-09
I solved slow firefox by typing in browser command line "about:config" without Quotation marks. I found the line  network.dns.disablelPv6  and right click the mouse and then toggled the line to be true. It worked like a charm. But be careful working with this or you can disable browser.
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567) This is the thread I used per lovinlunix advice in this thread. Thanks for the help guys it is invaluable to us for all the help!!

---

### Post by retiree on 2010-06-13
I have been out of town for a few days and returned and tried to fix flash with Flash-Aid and it still tells me I have a broken package in bad state, and to fix it first. How do I fix this? Thanks again for the help LovingLinux. Please be specific as I'm not proficient in Ubuntu. When I try to remove broken package it tells me to reinstall it first before I try to remove it, because it is in bad state. Doesn't make sense to me but, I don't what else to do. Thanks for the help

---

### Post by lovinglinux on 2010-06-13
> **retiree said:**
> I have been out of town for a few days and returned and tried to fix flash with Flash-Aid and it still tells me I have a broken package in bad state, and to fix it first. How do I fix this? Thanks again for the help LovingLinux. Please be specific as I'm not proficient in Ubuntu. When I try to remove broken package it tells me to reinstall it first before I try to remove it, because it is in bad state. Doesn't make sense to me but, I don't what else to do. Thanks for the help

Please post the errors from the terminal.

---

### Post by retiree on 2010-06-14
I ran the auto install from flash-aid website and it doesn't run from terminal. All I get is I must reinstall the old flash-plugin before attempting to install new flash player plugin. It did attempt to install new flash-plugin but it gave me the error message to reinstall the old plugin first. Thanks

---

### Post by retiree on 2010-06-14
Here is the terminal screen. I ran the attached thumbnails first and then ran the other terminal. It still doesn't work, What to do!!


clayton@clayton-desktop:~$ sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
[sudo] password for clayton: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 454FEDB228E1455D687C9CBE35DA01C261E46227
gpg: requesting key 61E46227 from hkp server keyserver.ubuntu.com
gpg: key 61E46227: public key "Launchpad Default PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/ jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/ jaunty/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [189B]                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]              
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,203B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [9,852B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages      
Get:6 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [2,955B]      
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [651B]
Fetched 79.4kB in 1s (61.6kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin64-installer: Conflicts: flashplugin-nonfree
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
clayton@clayton-desktop:~$

---

### Post by philinux on 2010-06-14
> **retiree said:**
> I just did an upgrade from Hardy Heron to Lucid Lynx and everything runs good except for an error that says "Flashplugin-nonfree. Package is in a very bad inconsistent state- you should reinstall it before attempting a removal. Also flash does still work but very slow to load. Firefox is slower than my Hardy install. What is a solution to this? Running 64 bit on both Hardy and now Lucid Lynx, Thanks

This a known upgrade bug. Please see the General Help forum sticky.

---

### Post by retiree on 2010-06-15
Thanks to PhilLunix I now have flash, but with no sound. Is there a work around for this? Thanks for all the help.

---

### Post by retiree on 2010-06-17
I found the solution to no sound!!! I don't how it got checked, but a mute selection was checked. I didn't even know that under "System- Preferences" there was a "sound" choice. I over looked it for 2 days looking for a "driver" to restore my sound. I am embarrassed to admit it,but sometimes eating crow is not a bad thing :lolflag: A BIG "Hardy" -pun intended-, thanks for all who helped. Great OS

---

