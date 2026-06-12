---
title: "Looking for a update errors troubleshooting tutorial"
date: 2010-08-04
forum: General Help
---

### Post by lunatico on 2010-08-04
Hello,

I have had similar problems to this for many years and today I have decided to find out why and how to fix them when they happen.

At the moment when I do 'sudo aptitude update' I get the following with some errors:
```
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]
Get:2 http://ppa.launchpad.net lucid Release.gpg [307B]                                                            
Get:3 http://ppa.launchpad.net lucid Release.gpg [307B]                                                            
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ lucid/main Translation-en_IE                               
Hit http://archive.canonical.com lucid Release.gpg                                                                 
Hit http://ppa.launchpad.net lucid Release.gpg                                                                     
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_IE                                           
Ign http://ppa.launchpad.net/llyzs/ppa/ubuntu/ lucid/main Translation-en_IE                                        
Hit http://archive.canonical.com lucid Release                                                                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                     
Ign http://ppa.launchpad.net/wvengen/ppa/ubuntu/ lucid/main Translation-en_IE                                      
Hit http://archive.canonical.com lucid/partner Packages                                                            
Hit http://archive.canonical.com lucid/partner Sources                                                             
Hit http://packages.medibuntu.org lucid Release.gpg                                                                
Hit http://ppa.launchpad.net lucid Release.gpg                                                                     
Ign http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main Translation-en_IE                   
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_IE                                       
Ign http://packages.medibuntu.org/ lucid/free Translation-en_IE                                            
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_IE                                                
Hit http://ppa.launchpad.net lucid Release.gpg                                                                     
Hit http://packages.medibuntu.org lucid Release                                                                    
Hit http://downloads.sourceforge.net all Release.gpg                                                           
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ lucid/main Translation-en_IE                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                     
Hit http://ie.archive.ubuntu.com lucid Release.gpg                                                                 
Hit http://packages.medibuntu.org lucid/free Packages                                                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_IE                                  
Hit http://packages.medibuntu.org lucid/non-free Packages                                                          
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IE                                              
Get:4 http://ppa.launchpad.net lucid Release [57.3kB]                                                              
Get:5 http://ppa.launchpad.net lucid Release [57.3kB]                                                              
Ign http://ppa.launchpad.net lucid Release                                                                         
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IE                                        
Hit http://packages.medibuntu.org lucid/free Sources                                                               
Hit http://ppa.launchpad.net lucid Release                                                                         
Hit http://packages.medibuntu.org lucid/non-free Sources                                                           
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IE                                          
Hit http://ppa.launchpad.net lucid Release                                                                         
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IE                                        
Hit http://ppa.launchpad.net lucid Release                                                                         
Hit http://ppa.launchpad.net lucid Release                                                                         
Hit http://ie.archive.ubuntu.com lucid-updates Release.gpg                                                         
Hit http://ppa.launchpad.net lucid Release                                                                    
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IE                                      
Get:6 http://ppa.launchpad.net lucid/main Packages [3,704B]                                                        
Get:7 http://ppa.launchpad.net lucid/main Packages [3,704B]                                                        
Get:8 http://ppa.launchpad.net lucid/main Packages [3,704B]                                                        
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IE                                
Get:9 http://ppa.launchpad.net lucid/main Packages [3,704B]                                                        
Get:10 http://ppa.launchpad.net lucid/main Packages [3,704B]                                                       
Get:11 http://ppa.launchpad.net lucid/main Packages [3,704B]                                       
99% [11 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]  
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ppa.launchpad.net lucid/main Packages                                                                 
  Sub-process /bin/bzip2 returned an error code (2)
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IE                                
Get:12 http://ppa.launchpad.net lucid/main Sources [1,420B]                                                        
Get:13 http://ppa.launchpad.net lucid/main Sources [1,420B]                                                        
Get:14 http://ppa.launchpad.net lucid/main Sources [1,420B]                                       
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IE               
Get:15 http://ppa.launchpad.net lucid/main Sources [1,420B]                                       
Hit http://downloads.sourceforge.net all Release                                                  
Get:16 http://ppa.launchpad.net lucid/main Sources [1,420B]                                       
Get:17 http://ppa.launchpad.net lucid/main Sources [1,420B]                                    
Get:18 http://ppa.launchpad.net lucid/main Sources [1,420B]                                                        
Get:19 http://ppa.launchpad.net lucid/main Sources [1,420B]                                                        
99% [19 Sources bzip2 0] [Waiting for headers] [Waiting for headers] [Connecting to ppa.launchpad.net (91.189.90.21
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ppa.launchpad.net lucid/main Sources                                                                    
  Sub-process /bin/bzip2 returned an error code (2)
Get:20 http://ie.archive.ubuntu.com lucid-security Release.gpg [189B]                                              
Hit http://ppa.launchpad.net lucid/main Packages                                                                   
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IE                                     
Hit http://ppa.launchpad.net lucid/main Packages                                                                   
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IE                               
Ign http://downloads.sourceforge.net all/main Packages                                                             
Hit http://ppa.launchpad.net lucid/main Sources                      
Hit http://ppa.launchpad.net lucid/main Packages                                                                   
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IE                                 
Hit http://ppa.launchpad.net lucid/main Packages                                                                   
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IE                               
Hit http://ppa.launchpad.net lucid/main Sources                                                                    
Ign http://downloads.sourceforge.net all/main Packages                                                             
Hit http://ie.archive.ubuntu.com lucid Release                                                                     
Hit http://ppa.launchpad.net lucid/main Packages                                                                   
Hit http://ie.archive.ubuntu.com lucid-updates Release                                                             
Get:21 http://ie.archive.ubuntu.com lucid-security Release [38.5kB]                                                
Get:22 http://ie.archive.ubuntu.com lucid-security Release [38.5kB]          
Get:23 http://ie.archive.ubuntu.com lucid-security Release [38.5kB]          
Ign http://ie.archive.ubuntu.com lucid-security Release                      
Hit http://ie.archive.ubuntu.com lucid/main Packages                   
Hit http://ie.archive.ubuntu.com lucid/restricted Packages                                          
Hit http://ie.archive.ubuntu.com lucid/restricted Sources                                                          
Hit http://ie.archive.ubuntu.com lucid/main Sources                                                                
Hit http://ie.archive.ubuntu.com lucid/multiverse Sources                                                          
Hit http://downloads.sourceforge.net all/main Packages                                                             
Hit http://ie.archive.ubuntu.com lucid/universe Sources                                             
Hit http://ie.archive.ubuntu.com lucid/universe Packages                      
Hit http://ie.archive.ubuntu.com lucid/multiverse Packages                    
Hit http://ie.archive.ubuntu.com lucid-updates/main Packages                  
Hit http://download.sip-communicator.org unstable/ Release.gpg                
Hit http://ie.archive.ubuntu.com lucid-updates/restricted Packages                     
Ign http://download.sip-communicator.org/deb/ unstable/ Translation-en_IE              
Hit http://ie.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://download.sip-communicator.org unstable/ Release
Hit http://ie.archive.ubuntu.com lucid-updates/main Sources
Hit http://download.sip-communicator.org unstable/ Packages
Hit http://ie.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://ie.archive.ubuntu.com lucid-updates/universe Sources
Hit http://ie.archive.ubuntu.com lucid-updates/universe Packages
Hit http://ie.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://ie.archive.ubuntu.com lucid-security/main Packages
Hit http://ie.archive.ubuntu.com lucid-security/restricted Packages
Hit http://ie.archive.ubuntu.com lucid-security/restricted Sources
Get:24 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:25 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:26 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:27 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:28 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:29 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:30 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:31 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:32 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:33 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:34 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:35 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:36 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:37 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:38 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:39 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:40 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:41 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:42 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:43 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:44 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:45 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:46 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:47 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:48 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:49 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:50 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:51 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:52 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:53 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:54 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:55 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:56 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:57 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:58 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:59 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
Get:60 http://ie.archive.ubuntu.com lucid-security/main Sources [17.3kB]
99% [60 Sources bzip2 0] [Connecting to ie.archive.ubuntu.com (193.1.193.69)]
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ie.archive.ubuntu.com lucid-security/main Sources                 
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://ie.archive.ubuntu.com lucid-security/multiverse Sources           
Hit http://ie.archive.ubuntu.com lucid-security/universe Sources
Hit http://ie.archive.ubuntu.com lucid-security/universe Packages
Hit http://ie.archive.ubuntu.com lucid-security/multiverse Packages
Fetched 3,071B in 5s (517B/s)                           
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 2
W: GPG error: http://ie.archive.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 2


```

What I'm looking for is some kind of howto or tutorial on how to understand and troubleshoot this. Can anyone help?

Thanks in advance!

---

### Post by lunatico on 2010-08-16
Anyone?

How to fix the BADSIG errors? Now I'm getting:

```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: BADSIG 5A9BF3BB4E5E17B5 Launchpad PPA for chromium-daily
W: GPG error: http://ie.archive.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Thanks!

---

### Post by lunatico on 2010-08-27
This commands seem to help.

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

---

### Post by lunatico on 2010-09-13
Also, when getting GPG signature errors do:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <hex number from the error output>
```

---

