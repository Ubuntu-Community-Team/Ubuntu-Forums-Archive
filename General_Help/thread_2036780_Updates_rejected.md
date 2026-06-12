---
title: "Updates rejected"
date: 2012-08-02
forum: General Help
---

### Post by kjbox on 2012-08-02
I have received notification of 8 updates all related to VLC, 7 security and 1 reccommended.

When trying to install I get a message saying that action would require installation of packages from 'not authenticated sources'. Details of this show that the problem package is the reccommended one - libcrystalhd3.

Even when I remove this from the list of updates to install I still get the same message and installation cannot procede.

How can I overcome this? Any help greatly appreciated.

Thanks.

---

### Post by plucky on 2012-08-03
> **kjbox said:**
> I have received notification of 8 updates all related to VLC, 7 security and 1 reccommended.

When trying to install I get a message saying that action would require installation of packages from 'not authenticated sources'. Details of this show that the problem package is the reccommended one - libcrystalhd3.

Even when I remove this from the list of updates to install I still get the same message and installation cannot procede.

How can I overcome this? Any help greatly appreciated.

Thanks.

Open a terminal and run ```
sudo apt-get update && sudo apt-get upgrade
``` and post back the output to the forum between 

[noparse]```
Your text here
```[/noparse] 

brackets.

Good luck

---

### Post by kjbox on 2012-08-03
Thanks for the reply. Here is the readout:

```

charles@charles-UX31E:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for charles: 
Ign http://my.archive.ubuntu.com precise InRelease                             
Ign http://my.archive.ubuntu.com precise-updates InRelease                     
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://my.archive.ubuntu.com precise-backports InRelease                   
Hit http://my.archive.ubuntu.com precise Release.gpg                           
Ign http://archive.canonical.com precise InRelease                             
Get:1 http://my.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://my.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://my.archive.ubuntu.com precise Release                               
Hit http://my.archive.ubuntu.com precise-updates Release                       
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://my.archive.ubuntu.com precise-updates Release                       
Hit http://extras.ubuntu.com precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://my.archive.ubuntu.com precise-backports Release                     
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://my.archive.ubuntu.com precise/main Sources                          
Hit http://archive.canonical.com precise Release                               
Hit http://my.archive.ubuntu.com precise/restricted Sources                    
Hit http://my.archive.ubuntu.com precise/universe Sources                      
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://my.archive.ubuntu.com precise/multiverse Sources                    
Hit http://my.archive.ubuntu.com precise/main i386 Packages                    
Hit http://my.archive.ubuntu.com precise/restricted i386 Packages              
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://my.archive.ubuntu.com precise/universe i386 Packages                
Hit http://my.archive.ubuntu.com precise/multiverse i386 Packages              
Ign http://dl.google.com stable InRelease                                      
Get:5 http://security.ubuntu.com precise-security/main Sources [34.0 kB]
Hit http://my.archive.ubuntu.com precise/main TranslationIndex                 
Ign http://dl.google.com stable InRelease                                      
Hit http://my.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://my.archive.ubuntu.com precise/restricted TranslationIndex           
Get:6 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://my.archive.ubuntu.com precise/universe TranslationIndex             
Get:7 http://dl.google.com stable Release.gpg [198 B]                          
Get:8 http://dl.google.com stable Release                                      
Ign http://my.archive.ubuntu.com precise-updates/main Sources/DiffIndex        
Get:9 http://security.ubuntu.com precise-security/restricted Sources [14 B]    
Get:10 http://dl.google.com stable Release                                     
Ign http://my.archive.ubuntu.com precise-updates/restricted Sources/DiffIndex  
Ign http://my.archive.ubuntu.com precise-updates/universe Sources/DiffIndex    
Get:11 http://dl.google.com stable/main i386 Packages [1,220 B]                
Ign http://dl.google.com stable/main TranslationIndex                          
Get:12 http://security.ubuntu.com precise-security/universe Sources [9,561 B]  
Ign http://my.archive.ubuntu.com precise-updates/multiverse Sources/DiffIndex  
Get:13 http://dl.google.com stable/main i386 Packages [464 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://my.archive.ubuntu.com precise-updates/main i386 Packages/DiffIndex  
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Ign http://my.archive.ubuntu.com precise-updates/restricted i386 Packages/DiffIndex
Ign http://my.archive.ubuntu.com precise-updates/universe i386 Packages/DiffIndex
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [125 kB]
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [31.9 kB]
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:18 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:19 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:20 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:21 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:22 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:23 http://security.ubuntu.com precise-security/universe Translation-en [20.3 kB]
Ign http://my.archive.ubuntu.com precise-updates/multiverse i386 Packages/DiffIndex
Hit http://my.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://my.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://my.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://my.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://my.archive.ubuntu.com precise-backports/main Sources
Hit http://my.archive.ubuntu.com precise-backports/restricted Sources
Hit http://my.archive.ubuntu.com precise-backports/universe Sources
Hit http://my.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://my.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://my.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://my.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://my.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://my.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://my.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://my.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://my.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://my.archive.ubuntu.com precise/main Translation-en
Hit http://my.archive.ubuntu.com precise/multiverse Translation-en
Hit http://my.archive.ubuntu.com precise/restricted Translation-en
Hit http://my.archive.ubuntu.com precise/universe Translation-en
Hit http://my.archive.ubuntu.com precise-updates/main Sources
Hit http://my.archive.ubuntu.com precise-updates/restricted Sources
Hit http://my.archive.ubuntu.com precise-updates/universe Sources
Hit http://my.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://my.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://my.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://my.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://my.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://my.archive.ubuntu.com precise-updates/main Translation-en
Hit http://my.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://my.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://my.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://my.archive.ubuntu.com precise-backports/main Translation-en
Hit http://my.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://my.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://my.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 278 kB in 47s (5,864 B/s)
Reading package lists... Done
W: GPG error: http://my.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse
The following packages will be upgraded:
  libvlc5 libvlccore5 vlc-data
3 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 9,577 kB of archives.
After this operation, 2,470 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/universe libvlccore5 i386 2.0.3-0ubuntu0.12.04.1 [468 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/universe vlc-data all 2.0.3-0ubuntu0.12.04.1 [9,058 kB]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/universe libvlc5 i386 2.0.3-0ubuntu0.12.04.1 [51.0 kB]
Fetched 9,577 kB in 1min 9s (137 kB/s)                                         
(Reading database ... 260103 files and directories currently installed.)
Preparing to replace libvlccore5 2.0.1-4 (using .../libvlccore5_2.0.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libvlccore5 ...
Preparing to replace vlc-data 2.0.1-4 (using .../vlc-data_2.0.3-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement vlc-data ...
Preparing to replace libvlc5 2.0.1-4 (using .../libvlc5_2.0.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libvlc5 ...
Processing triggers for hicolor-icon-theme ...
Setting up vlc-data (2.0.3-0ubuntu0.12.04.1) ...
Setting up libvlccore5 (2.0.3-0ubuntu0.12.04.1) ...
Setting up libvlc5 (2.0.3-0ubuntu0.12.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
charles@charles-UX31E:~$ 

```

Just noticed that after running the upgrade/update the number of packages in the update manager waiting to be installed has dropped to 5, 4 security and the 1 reccommended. The 4 security ones are: multimedia player and streamer vlc, multimedia player and streamer (without X controls nox-vlc, vlc-plugin-notify and vlc-plugin-pulse.

---

### Post by plucky on 2012-08-03
> W: GPG error: [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

Look for a two entries for the "partner" repositories in your Sources.list and remove one of them.

You may have to run from a terminal ```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
``` to delete the broken .list files and then reload with the "update" command.

To fix the GPG error,try temporarily switching to the Main Server in Software Sources and running from a terminal ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Post back if still getting any errors.

Remember to switch back to your local repository for faster downloads.

Good luck

---

### Post by kjbox on 2012-08-06
Sorry about delay in replyig, I was away for the weekend.

I opened /var/lib/apt/lists/ and found the sources.list but could not see any duplication there, and it came up as read only so I could not have edited it anyway. Obviously I was looking in the wrong place or using an incorrect method, please let me know how to edit the Sources.list.

Also, where do I change the repositery I download from?

I now have 33 updates stacked up waiting to install, even unchecking all the 5 related to vlc does not help as I still get the 'non authenticated source' warning and download/install aborts.

Thanks in advance.

---

### Post by plucky on 2012-08-06
> **kjbox said:**
> Sorry about delay in replyig, I was away for the weekend.

I opened /var/lib/apt/lists/ and found the sources.list but could not see any duplication there, and it came up as read only so I could not have edited it anyway. Obviously I was looking in the wrong place or using an incorrect method, please let me know how to edit the Sources.list.

Also, where do I change the repositery I download from?

I now have 33 updates stacked up waiting to install, even unchecking all the 5 related to vlc does not help as I still get the 'non authenticated source' warning and download/install aborts.

Thanks in advance.

Your sources.list is located in **/etc/apt/sources.list**

To edit it you need to use ```
gksudo gedit /etc/apt/sources.list
```

Other Sources also exist in the /etc/apt/sources.list.d/ directory,for instance Medibuntu,PPA'S etc,so look in that directory also.

You can also use the GUI by accessing the **Settings** button in the Update Manager.

Once Software Sources is open,on the first TAG is the button to change the Download Server.

Good luck

---

### Post by Kundan Negi on 2012-08-06
It seems your lib file need to fixed. Type this in your Terminal
 sudo apt-get install -f
Hope it helps you

---

### Post by kjbox on 2012-08-06
Thanks Plucky, found the Sources.list and edited it accordingly, did an update and dist-upgrade from the main server.

All went smoothly and all outstanding updates were installed :D

Again, many thanks

---

### Post by tisaari on 2012-09-08
I'm running into the same problem with Linux Mint release 13 (Maya) running Cinnamon.

apt-get update says:
```
 sudo apt-get update
Ign http://linuxmint.bio.lmu.de maya InRelease
Ign http://archive.canonical.com precise InRelease                             
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://archive.ubuntu.com precise-updates InRelease                        
Hit http://linuxmint.bio.lmu.de maya Release.gpg                               
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release                               
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://linuxmint.bio.lmu.de maya Release                                   
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://archive.ubuntu.com precise Release                                  
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://linuxmint.bio.lmu.de maya/main amd64 Packages                       
Get:4 http://security.ubuntu.com precise-security/main amd64 Packages [158 kB] 
Get:5 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Hit http://linuxmint.bio.lmu.de maya/upstream amd64 Packages                   
Hit http://linuxmint.bio.lmu.de maya/import amd64 Packages                     
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://linuxmint.bio.lmu.de maya/main i386 Packages                        
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://linuxmint.bio.lmu.de maya/upstream i386 Packages                    
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Get:6 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Hit http://linuxmint.bio.lmu.de maya/import i386 Packages                      
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Get:7 http://security.ubuntu.com precise-security/universe amd64 Packages [41.8 kB]
Ign http://linuxmint.bio.lmu.de maya/import TranslationIndex                   
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Get:8 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,180 B]
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Ign http://linuxmint.bio.lmu.de maya/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Get:9 http://security.ubuntu.com precise-security/main i386 Packages [163 kB]  
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Ign http://linuxmint.bio.lmu.de maya/upstream TranslationIndex                 
Get:10 http://archive.ubuntu.com precise-updates/main amd64 Packages [377 kB]  
Get:11 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [6,755 B]
Get:12 http://archive.ubuntu.com precise-updates/universe amd64 Packages [127 kB]
Get:13 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:14 http://security.ubuntu.com precise-security/universe i386 Packages [42.0 kB]
Get:15 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:16 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Get:17 http://archive.ubuntu.com precise-updates/main i386 Packages [381 kB]   
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://linuxmint.bio.lmu.de maya/import Translation-en_US                  
Ign http://linuxmint.bio.lmu.de maya/import Translation-en                     
Ign http://linuxmint.bio.lmu.de maya/main Translation-en_US                    
Ign http://linuxmint.bio.lmu.de maya/main Translation-en                       
Get:18 http://archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Ign http://linuxmint.bio.lmu.de maya/upstream Translation-en_US                
Ign http://linuxmint.bio.lmu.de maya/upstream Translation-en                   
Get:19 http://archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Get:20 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://packages.medibuntu.org precise InRelease                       
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages          
Ign http://packages.medibuntu.org precise/free TranslationIndex           
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Ign http://deb.opera.com stable InRelease                                      
Err http://deb.opera.com stable Release.gpg         
  Unable to connect to deb.opera.com:http:
Ign http://deb.opera.com stable Release
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex
Ign http://deb.opera.com stable/non-free TranslationIndex
Err http://deb.opera.com stable/non-free amd64 Packages
  Unable to connect to deb.opera.com:http:
Err http://deb.opera.com stable/non-free i386 Packages
  Unable to connect to deb.opera.com:http:
Err http://deb.opera.com stable/non-free Translation-en_US
  Unable to connect to deb.opera.com:http:
Err http://deb.opera.com stable/non-free Translation-en
  Unable to connect to deb.opera.com:http:
Fetched 1,561 kB in 1min 3s (24.7 kB/s)
W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Unable to connect to deb.opera.com:http:

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-amd64/Packages  Unable to connect to deb.opera.com:http:

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages  Unable to connect to deb.opera.com:http:

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en_US  Unable to connect to deb.opera.com:http:

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en  Unable to connect to deb.opera.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

```and apt-get dist-upgrade says:
```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libcrystalhd3 linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic
  linux-image-3.2.0-30-generic
The following packages will be upgraded:
  libvlc5 libvlccore5 linux-generic linux-headers-generic linux-image-generic
  vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
10 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.7 MB/64.9 MB of archives.
After this operation, 219 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Err http://archive.ubuntu.com/ubuntu/ precise-updates/universe vlc-plugin-pulse amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe vlc-plugin-pulse amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe vlc-plugin-notify amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe vlc-nox amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe vlc amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.190 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe libvlccore5 amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe vlc-data all 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/universe libvlc5 amd64 2.0.3-0ubuntu0.12.04.1
  403  Forbidden [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_2.0.3-0ubuntu0.12.04.1_amd64.deb  403  Forbidden [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-notify_2.0.3-0ubuntu0.12.04.1_amd64.deb  403  Forbidden [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_2.0.3-0ubuntu0.12.04.1_amd64.deb  403  Forbidden [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_2.0.3-0ubuntu0.12.04.1_amd64.deb  403  Forbidden [IP: 91.189.92.190 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore5_2.0.3-0ubuntu0.12.04.1_amd64.deb  403  Forbidden [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_2.0.3-0ubuntu0.12.04.1_all.deb  403  Forbidden [IP: 91.189.92.184 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc5_2.0.3-0ubuntu0.12.04.1_amd64.deb  403  Forbidden [IP: 91.189.92.184 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```Seems like that security-source is completely blocked. The packages in question are the same as with the OP.

sources.list:
```
deb http://linuxmint.bio.lmu.de/packages/ maya main upstream import
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner
deb http://packages.medibuntu.org/ precise free non-free

# deb http://archive.getdeb.net/ubuntu precise-getdeb apps
# deb http://archive.getdeb.net/ubuntu precise-getdeb games
```

---

