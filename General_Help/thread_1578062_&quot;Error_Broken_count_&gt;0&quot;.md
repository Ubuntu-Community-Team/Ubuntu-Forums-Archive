---
title: "&quot;Error Broken count &gt;0&quot;"
date: 2010-09-19
forum: General Help
---

### Post by m455 on 2010-09-19
I've recently ran into a problem installing applications. I am getting a "Error Broken count >0" error message stating to start Package Manager.

System / Administration / Synaptic Package Manager then gives the error: You Have 1 Broken package on your system! Use the “Broken” filter to locate it. When I search under broken it shows “smbclient” when I try to mark it for removal and apply it states that not all changes and updates succeeded. The details show the following:

(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
Setting up grub-pc (1.98-1ubuntu7) ...
Installation finished. No error reported.
cp: reading `/usr/share/grub/unicode.pf2': Input/output error
dpkg: error processing grub-pc (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
grub-pc

I've tried running  sudo apt-get -f install  and it returns:

Reading package lists... Done
Building dependency tree*
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
samba-common smbclient
Suggested packages:
smbfs
The following packages will be upgraded:
samba-common smbclient
2 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
Need to get 11.9MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1*[http://us.archive.ubuntu.com/ubuntu/*lucid-updates/main](http://us.archive.ubuntu.com/ubuntu/*lucid-updates/main) smbclient 2:3.4.7~dfsg-1ubuntu3.2 [11.5MB]
Get:2*[http://us.archive.ubuntu.com/ubuntu/*lucid-updates/main](http://us.archive.ubuntu.com/ubuntu/*lucid-updates/main) samba-common 2:3.4.7~dfsg-1ubuntu3.2 [396kB]
Fetched 11.9MB in 45s (261kB/s)*
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by robsoles on 2010-09-20
please try following in terminal
```
sudo apt-get update
```
If the word error is in the output of that command then please post back the ENTIRE output from the command in terminal.

If the word 'error' is absent from the output of that one please try;
```
sudo apt-get remove smbclient
sudo apt-get install smbclient
```

Stop at the first one if it produces errors and post back ALL of the output, again post back ALL output of command if it gets an error from the second one.

---

### Post by m455 on 2010-09-20
Thanks for the response. After running sudo apt-get update the only error it showed was Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
  404  Not Found


m455@m455:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/c-korn/vlc/ubuntu/](http://ppa.launchpad.net/c-korn/vlc/ubuntu/) lucid/main Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
W: Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
m455@m455:~$

---

### Post by robsoles on 2010-09-20
For now it might be best if you edit /etc/apt/sources.list and put a # at the start of each line that draws a '404 Not Found' error.

Make a backup of the file first:
```
sudo 'cp /etc/apt/sources.list /etc/apt/sources.list.my-backup'
```

Then place the '#'s and then try the other pair of commands I offered you in my first post:
```

sudo apt-get remove smbclient
sudo apt-get install smbclient
```

If an error occurs don't do next command but of course post resulting output back to this thread please.

If no error occurs you may as well check for updatability:
```
sudo apt-get update
sudo apt-get upgrade
```
(same deal regarding errors!)

---

