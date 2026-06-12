---
title: "An unhandable error occured...in aptdaemon, noResume from RAM , Nvidia critical error"
date: 2011-04-05
forum: General Help
---

### Post by holmziep on 2011-04-05
Hi folks, I have this and a few other issues I am hoping we can work out, which may be related to each other?  This is LONG post, sorry...Beginner here.

I have been having a resume from suspend (to RAM) problem all along.  I also have a aptdaemon problem.  And, to top it off, I now my boot is NOW delayed some 20 seconds, with a "Resume Libgcrypt 1.4.5" on the screen, happened after I installed "Hibernate" ("sudo apt-get install hibernate")

I did the following which I saw in some recent threads:

First I tried adding this command to the grub:

GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" 
That didn't work so I changed it back.

I also ran "quirk-checker.sh" from Launchpad Librarian, and came up with a message, "CRITICAL ERROR: Using nvidia binary driver. This is not supported".  (have read about video drivers causing problems, but otherwise seems to work with the additional special effects, etc.)

Discovered aptdaemon problem when I tried to install a Ham Radio application "wspr_2.00r1714_i386.deb" (after downloading and opening it with Ubuntu Software Center).   I get this: "AN UNHANDLABLE ERROR OCCURED: There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry."

Had no problem previously installing other applications over the last few weeks, but DIRECTLY from the Software Center.  My Ubuntu 10.10 desktop install (6 weeks old?) has been updated regularly.  Just did it again, now.

I read other having same issue, thus was directed to "Package Manager Troubleshooting Procedure" hoping that it may help "US" determine why I get the error message when trying to load an application. 

(FYI, This is a revived Dell dimension 8300, 1 gig ram, Ubuntu drive installed at primary master PATA  position, video: Nvidia FX5200 , Ubuntu updated video driver to v173,13.28.  Have an XP system hard drive in primary SATA postion,   I can select UBUNTU boot by pressing F12 and selecting 3 (PATA primary Master hard drive).  Ubuntu runs GREAT but for the RESUME from suspend to ram.  (Need to hold the power button down for 8 seconds and start over or set power management to "NEVER".)  Resume works in xp fine.

Super Kudos to all out there, I am soon to be a supporter as soon as I get a job.  (I AM going to learn this Lenix thing, failure  is NOT an OPTION!!)

Tks! 
--------------------------------------------------------
Here is copy of Package Manager Troubleshooting Procedure: (had to start over once, hope i didn't mess it up)  (Did this last week)

holmzie@holmzie-Dimension-8300:~$ sudo fuser -vvv /var/lib/dpkg/lock
[sudo] password for holmzie: 
holmzie@holmzie-Dimension-8300:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
holmzie@holmzie-Dimension-8300:~$ uname -a
Linux holmzie-Dimension-8300 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
holmzie@holmzie-Dimension-8300:~$ sudo rm /var/lib/apt/lists/lock
rm: cannot remove `/var/lib/apt/lists/lock': No such file or directory
holmzie@holmzie-Dimension-8300:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
holmzie@holmzie-Dimension-8300:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
holmzie@holmzie-Dimension-8300:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
holmzie@holmzie-Dimension-8300:~$ sudo rm -rf /var/lib/dpkg/updates/*
holmzie@holmzie-Dimension-8300:~$ sudo rm -rf /var/lib/apt/lists
holmzie@holmzie-Dimension-8300:~$ sudo rm /var/cache/apt/*.bin
holmzie@holmzie-Dimension-8300:~$ sudo mkdir /var/lib/apt/lists
holmzie@holmzie-Dimension-8300:~$ sudo mkdir /var/lib/apt/lists/partial
holmzie@holmzie-Dimension-8300:~$ 
holmzie@holmzie-Dimension-8300:~$ 
holmzie@holmzie-Dimension-8300:~$ LANG=C;sudo apt-get clean
holmzie@holmzie-Dimension-8300:~$ LANG=C;sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
holmzie@holmzie-Dimension-8300:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en           
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]           
Ign [http://ppa.launchpad.net/kamalmostafa/fldigi/ubuntu/](http://ppa.launchpad.net/kamalmostafa/fldigi/ubuntu/) maverick/main Translation-en
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9762B]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9743B]                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg [198B]           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [747B]                
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources [668B]                   
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [700B]             
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [770B]             
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [31.4kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release [31.4kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources [829kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4370B]           
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4179kB]            
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources [151kB]           
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1492kB]          
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5992B]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [5791kB]      
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]     
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources [90.7kB]        
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources [778B]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources [36.2kB]    
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources [1498B]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [251kB]   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages [1797B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages [107kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages [2834B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources [31.0kB]       
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources [14B]    
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources [12.1kB]   
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources [643B]   
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages [110kB]  
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages [49.5kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages [1659B]
Fetched 13.5MB in 2min 47s (80.6kB/s)                                          
Reading package lists... Done
holmzie@holmzie-Dimension-8300:~$ sudo dpkg --clear-avail
holmzie@holmzie-Dimension-8300:~$ sudo dpkg --configure -a
holmzie@holmzie-Dimension-8300:~$ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
holmzie@holmzie-Dimension-8300:~$ LANG=C;sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
holmzie@holmzie-Dimension-8300:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/kamalmostafa/fldigi/ubuntu/](http://ppa.launchpad.net/kamalmostafa/fldigi/ubuntu/) maverick/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
holmzie@holmzie-Dimension-8300:~$ unhandlable error                            
unhandlable: command not found
----------------------------------------------------------------

At this point I tried something someone else did in a Ubunto Forum:

holmzie@holmzie-Dimension-8300:~$ cd ~/Downloads; sudo dpkg -i ./wspr_2.00r1714_i386.deb
[sudo] password for holmzie: 
dpkg: error processing ./wspr_2.00r1714_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./wspr_2.00r1714_i386.deb
holmzie@holmzie-Dimension-8300:~/Downloads$ 
----------------------------------------------------------------
Hope I didn't mess things up.  Here is another attempt, install code from the the author of WSPR:

holmzie@holmzie-Dimension-8300:~$ sudo dpkg --instdir=. -i wspr_2.00r1714_i386.deb
dpkg: error processing wspr_2.00r1714_i386.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Errors were encountered while processing:
 wspr_2.00r1714_i386.deb
holmzie@holmzie-Dimension-8300:~$

---

