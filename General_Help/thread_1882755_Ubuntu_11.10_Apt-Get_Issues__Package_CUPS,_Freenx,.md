---
title: "Ubuntu 11.10 Apt-Get Issues :: Package CUPS, Freenx, CDROM?"
date: 2011-11-17
forum: General Help
---

### Post by own3mall on 2011-11-17
I'm having a couple of issues installing certain software and am getting prompted to install cdrom apt support?

Why am I getting warnings about apt-cdrom?  What does apt-cdrom do anyways?  Also, why are the packages not found for freenx?  Why can't it locate the package CUPS?  I am installing freenx manually from the instructions provided by the freenx team, and the freenx node complains about CUPS saying it's not installed.  Can anyone please help?

Why are the freenx packages not found?

Here's some info (sudo apt-get update):

```

eric@i7server:~/Documents$ sudo apt-get update
[sudo] password for eric: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release.gpg                                                       
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release                                                           
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex                                             
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex                                       
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages                                                
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages                                          
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US                                            
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en                                               
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US                                      
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en                                         
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                
Ign http://security.ubuntu.com oneiric-security InRelease                                                        
Ign http://us.archive.ubuntu.com oneiric InRelease                                         
Ign http://extras.ubuntu.com oneiric InRelease                                             
Ign http://archive.canonical.com oneiric InRelease                                         
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                                 
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                               
Hit http://archive.canonical.com oneiric Release.gpg                                       
Hit http://extras.ubuntu.com oneiric Release.gpg                                           
Hit http://security.ubuntu.com oneiric-security Release.gpg                                
Ign http://ppa.launchpad.net oneiric InRelease                                             
Hit http://us.archive.ubuntu.com oneiric Release.gpg                                       
Hit http://archive.canonical.com oneiric Release                                           
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                               
Hit http://security.ubuntu.com oneiric-security Release                                    
Hit http://extras.ubuntu.com oneiric Release                                               
Ign http://ppa.launchpad.net oneiric Release.gpg                                            
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                             
Hit http://archive.canonical.com oneiric/partner Sources                                   
Hit http://security.ubuntu.com oneiric-security/main Sources                               
Hit http://extras.ubuntu.com oneiric/main Sources                                          
Hit http://archive.canonical.com oneiric/partner i386 Packages                             
Ign http://archive.canonical.com oneiric/partner TranslationIndex                          
Hit http://security.ubuntu.com oneiric-security/restricted Sources                         
Hit http://security.ubuntu.com oneiric-security/universe Sources                           
Hit http://security.ubuntu.com oneiric-security/multiverse Sources                                               
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                                          
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                       
Hit http://security.ubuntu.com oneiric-security/main i386 Packages                         
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages                   
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                     
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages                   
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                      
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                      
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                      
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                        
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                              
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                        
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                        
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                    
Ign http://ppa.launchpad.net oneiric Release.gpg                                           
Ign http://ppa.launchpad.net oneiric Release                                               
Ign http://ppa.launchpad.net oneiric Release                         
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://us.archive.ubuntu.com oneiric-updates Release              
Hit http://us.archive.ubuntu.com oneiric-backports Release
Hit http://us.archive.ubuntu.com oneiric/main Sources                 
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/brianmercer/php/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/brianmercer/php/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Now on to the apt-cdrom part:

```


eric@i7server:~/Documents$ sudo apt-cdrom
apt 0.8.16~exp5ubuntu13 for i386 compiled on Oct  6 2011 15:25:44
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  --auto-detect Auto detect drive and mount point
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)
eric@i7server:~/Documents$ sudo apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [6fa406fb83a39501d16fb50996b09668-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?
eric@i7server:~/Documents$ sudo apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [5a0ebc8062b9fa709b4b30d3052acc42-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?
eric@i7server:~/Documents$ sudo apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [5a0ebc8062b9fa709b4b30d3052acc42-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?
eric@i7server:~/Documents$ sudo apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [5a0ebc8062b9fa709b4b30d3052acc42-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

```CUPS:

```

eric@i7server:~/Downloads$ sudo apt-get install CUPS
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package CUPS
eric@i7server:~/Downloads$ 


```Any help is appreciated!  Thanks!  :KS

---

### Post by own3mall on 2011-11-18
Anyone?

---

### Post by oldos2er on 2011-11-19
Try ```
sudo apt-get install cups
```

Assuming you don't want or need apt-cdrom, run ```
gksu /etc/apt/sources.list
``` and comment out or delete the lines at the top referencing the CD-ROM.

---

