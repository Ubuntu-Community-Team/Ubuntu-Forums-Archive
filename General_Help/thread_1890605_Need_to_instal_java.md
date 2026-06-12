---
title: "Need to instal java"
date: 2011-12-03
forum: General Help
---

### Post by Ketman on 2011-12-03
I'm using Ubuntu 9.10. 

So I've been to java.com and downloaded jre-6u18-linux-i586.bin. Then I tried to carry out the instructions for installing the RPM package, as described here:

**To install the Linux RPM file**

 Follow these instructions:

[LIST=1]
[*]**Become the root user** by running the su command and entering the super-user password. 
At the terminal: Type:
**su **
 Enter the root password.
[*]**Change to the directory in which you want to install.** Type:
**cd <directory>**
For example, to install the software in the /usr/java/ directory, Type:
**cd /usr/java**

***Note about root access:**  To install Java in a system-wide location such as**/usr/local**, you  must login as the root user to gain the necessary permissions. If you do  not have root access, install Java in your home directory or a  subdirectory for which you have write permissions.*
[*]**Change the permission of the file you downloaded to be executable.** Type:
  **chmod a+x jre-7u<version>-linux-i586-rpm.bin**
[/LIST]
And 3. is where it comes unstuck. I'm getting "No such file or directory" when I press enter. I've replaced "7u<version>" with "6u18", because that's what's on the downloaded filename - have I done something wrong?

---

### Post by oldtimer7777 on 2011-12-03
If you want to install Java JRE you can use this guide, and it is about 1/4th the way down the checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

RPMs are for Fedora, not Ubuntu.

---

### Post by Ketman on 2011-12-04
Thanks. I've followed the instructions, and this is what I get:-

ketman@ketman-laptop:~$ sudo add-apt-repository ppa:ferramroberto/java
[sudo] password for ketman: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 3E756CF119B127D4DA40A186B725097B3ACC3965
gpg: requesting key 3ACC3965 from hkp server keyserver.ubuntu.com
gpg: key 3ACC3965: "Launchpad lffl" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ketman@ketman-laptop:~$ sudo apt-get update
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_GB                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages            
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
  404  Not Found [IP: 91.189.92.167 80]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources     
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages          
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages          
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                 
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources           
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
  404  Not Found [IP: 91.189.92.167 80]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages            
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources       
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources 
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources    
  404  Not Found [IP: 91.189.92.167 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages  
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
ketman@ketman-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin unixodbc
Suggested packages:
  equivs ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming libmyodbc odbc-postgresql libct1
The following NEW packages will be installed
  gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts
  sun-java6-jre sun-java6-plugin unixodbc
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.8MB/36.8MB of archives.
After this operation, 106MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  java-common sun-java6-jre odbcinst1debian1 unixodbc sun-java6-bin
  gsfonts-x11 sun-java6-fonts sun-java6-plugin
Install these packages without verification [y/N]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main java-common 0.30ubuntu5
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse sun-java6-jre 6.24-1build0.9.10.1
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main odbcinst1debian1 2.2.11-16ubuntu1
  404  Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main unixodbc 2.2.11-16ubuntu1
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse sun-java6-jre 6.24-1build0.9.10.1
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse sun-java6-bin 6.24-1build0.9.10.1
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse sun-java6-fonts 6.24-1build0.9.10.1
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse sun-java6-plugin 6.24-1build0.9.10.1
  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu5_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu5_all.deb)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6.24-1build0.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6.24-1build0.9.10.1_all.deb)  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16ubuntu1_i386.deb)  404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16ubuntu1_i386.deb)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6.24-1build0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6.24-1build0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-fonts_6.24-1build0.9.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-fonts_6.24-1build0.9.10.1_all.deb)  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6.24-1build0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6.24-1build0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ketman@ketman-laptop:~$ 

I can't tell from that whether the operation was successful or not, but the number of "fail" lines tell me it wasn't. But I tried downloading something for which I need java, and got the message "It appears you do not have java installed". So I'm stuck again. Any ideas?

---

### Post by oldos2er on 2011-12-04
9.10 is no longer supported, its repositories are offline. I suggest you update to at least 10.04.

---

### Post by oldtimer7777 on 2011-12-04
> **oldos2er said:**
> 9.10 is no longer supported, its repositories are offline. I suggest you update to at least 10.04.

Oh that stinks..  Sorry I didn't know they were using 9.10..

---

### Post by Ketman on 2011-12-05
Thanks. I'll upgrade.

---

