---
title: "Complete noob to ubuntu."
date: 2011-11-15
forum: General Help
---

### Post by snypadub on 2011-11-15
I have been using Ubuntu since Sunday and am therefore, still an absolute noob.  Whilst I am really enjoying my new os, I am having certain problems. 

I have recently tried to install some drivers for a midi controller I have (hercules djcontroll mp3) and think I may have screwed something up because I am now getting errors all over the place.

I have no sound online, I am able to hear things through vlc and the like but youtube videos, soundcloud links etc. do not play sound in either Firefox or Chronium. 

I have done a sudo apt-get update (a process I don't understand at all) and it provides me with the following information:

```
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease         
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                           
Hit http://gb.archive.ubuntu.com oneiric-updates Release.gpg          
Hit http://security.ubuntu.com oneiric-security Release.gpg           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://gb.archive.ubuntu.com oneiric-updates Release                       
Hit http://gb.archive.ubuntu.com oneiric-backports Release                     
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://gb.archive.ubuntu.com oneiric/main Sources                          
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                      
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://gb.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB            
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en_GB   
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB
Ign http://extras.ubuntu.com oneiric/main Translation-en
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/mixxxdevelopers/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mixxxdevelopers/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Can anybody here, see what I have done wrong and talk me through the process of rectifying the situation. 

I don't consider myself to be stupid but, I feel like it with ubuntu. Really need a simple to understand noob tutorial for practically everything really. 

Thanks for your time. Being a new member here also, I am fully aware I may have posted this in the wrong place. Forgive my ignorance of this forum and rest assured, I fully intend to become a well versed and productive member here when I begin to understand ubuntu. 

:) 
Bless.

---

### Post by BillyBoa on 2011-11-15
apt-get upgrade is the command to download and install any upgrades from the Main Server.

Assuming you are using Ubuntu 11.10, go to upper left corner push dash and search for the "Software Sources". Open it.

There on the panel Other Software, uncheck the PPAs they give you problem, means

[http://ppa.launchpad.net/mixxxdevelopers/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mixxxdevelopers/ppa/ubuntu/dists/oneiric/main/source/Sources)

and

[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources)

Then press CTRL+ALT+T open a terminal and write

```
sudo apt-get update
```

Tell if the problem is solved

---

### Post by snypadub on 2011-11-15
Hey man, thanks for that. Unfortunately, the problem still doesn't seem to be resolved. I am certainly not getting any sound through youtube or soundcloud.

Feels really weird not knowing how to resolve an issue like this. Can't wait to be used to ubuntu.

---

### Post by BillyBoa on 2011-11-15
Well that was only the solution for the PPAs

To solve the problem of the sound, according to my opinion you should uninstall the drivers you installed.

You can do that through an application called Synaptic.

You can download Synaptic from the Ubuntu Software Center.
Then you find it from Dash search and execute it. Needs password.

From there you search (there are 2 search on the top, choose the right one with the lens) for the drivers you installed. Right click and choose uninstall.

Be sure to not uninstall other program.

---

### Post by snypadub on 2011-11-15
tried to install the synaptic package manager and met this error after install:

```
installArchives() failed: Selecting previously deselected package libept1. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 151033 files and directories currently installed.) 
Unpacking libept1 (from .../libept1_1.0.5build1_i386.deb) ... 
Selecting previously deselected package synaptic. 
Unpacking synaptic (from .../synaptic_0.75.2ubuntu8_i386.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for man-db ... 
Setting up hdjmod-dkms (1.28~dnjl4) ... 
Loading new hdjmod-1.28 DKMS files... 
Error! No valid dkms.conf in dkms_source_tree or dkms_binaries_only. 
/usr/src/hdjmod-1.28.dkms.tar.gz is not a valid DKMS tarball. 
dpkg: error processing hdjmod-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 7 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of hdjcpl: 
 hdjcpl depends on hdjmod-dkms (>= 1.27); however: 
  Package hdjmod-dkms is not configured yet. 
dpkg: error processing hdjcpl (--configure): 
 dependency problems - leaving unconfigured 
Setting up libept1 (1.0.5build1) ... 
No apport report written because MaxReports is reached already
Setting up synaptic (0.75.2ubuntu8) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 hdjmod-dkms 
 hdjcpl 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up hdjmod-dkms (1.28~dnjl4) ... 
Loading new hdjmod-1.28 DKMS files... 
Error! No valid dkms.conf in dkms_source_tree or dkms_binaries_only. 
/usr/src/hdjmod-1.28.dkms.tar.gz is not a valid DKMS tarball. 
dpkg: error processing hdjmod-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 7 
dpkg: dependency problems prevent configuration of hdjcpl: 
 hdjcpl depends on hdjmod-dkms (>= 1.27); however: 
  Package hdjmod-dkms is not configured yet. 
dpkg: error processing hdjcpl (--configure): 
 dependency problems - leaving unconfigured 

``` any ideas what i'm doing wrong?

---

### Post by raja.genupula on 2011-11-15
change your server from update manager and update again.

& do this also
sudo apt-get install -f
sudo apt-get update

---

### Post by BillyBoa on 2011-11-15
You have to run

```
sudo dpkg --configure -a
```

and

```
sudo apt-get -f install
```

---

### Post by snypadub on 2011-11-15
Cheers. How do I change my server from update manager??? Complete novice remember.

---

### Post by snypadub on 2011-11-15
> **BillyBoa said:**
> You have to run

```
sudo dpkg --configure -a
```and

```
sudo apt-get -f install
```

Ok followed your steps and got this as the result: 

```
root@joe-Compaq-Presario-CQ61-Notebook-PC:~# sudo dpkg --configure -a
Setting up hdjmod-dkms (1.28~dnjl4) ...
Loading new hdjmod-1.28 DKMS files...
Error! No valid dkms.conf in dkms_source_tree or dkms_binaries_only.
/usr/src/hdjmod-1.28.dkms.tar.gz is not a valid DKMS tarball.
dpkg: error processing hdjmod-dkms (--configure):
 subprocess installed post-installation script returned error exit status 7
dpkg: dependency problems prevent configuration of hdjcpl:
 hdjcpl depends on hdjmod-dkms (>= 1.27); however:
  Package hdjmod-dkms is not configured yet.
dpkg: error processing hdjcpl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hdjmod-dkms
 hdjcpl
root@joe-Compaq-Presario-CQ61-Notebook-PC:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up hdjmod-dkms (1.28~dnjl4) ...
Loading new hdjmod-1.28 DKMS files...
Error! No valid dkms.conf in dkms_source_tree or dkms_binaries_only.
/usr/src/hdjmod-1.28.dkms.tar.gz is not a valid DKMS tarball.
dpkg: error processing hdjmod-dkms (--configure):
 subprocess installed post-installation script returned error exit status 7
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of hdjcpl:
 hdjcpl depends on hdjmod-dkms (>= 1.27); however:
  Package hdjmod-dkms is not configured yet.
dpkg: error processing hdjcpl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 hdjmod-dkms
 hdjcpl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by BillyBoa on 2011-11-15
> **snypadub said:**
> Cheers. How do I change my server from update manager??? Complete novice remember.

Well let's see the solution of our friend raja.genupula.

To change server, find the Software Sources from the Dash Search.

Then open it and go to the first tab "Ubuntu Software".

Go down to Main Server tab and check to choose "Other"

from there there at right there is a tab "Select Best Server".

Push it and wait for a few minutes.

When stops push the right down tab "Choose Server" needs password.

Then copy paste the commands raja.genupula. told you.

---

### Post by Sigma1 on 2011-11-15
First thing, I think, is to uninstall the drivers, as people have suggested. That depends a bit on where they came from and how you installed them, though.
Apart from that, the fact that VLC gives you sound, makes me think that the problem is with the mp3 codecs etc., not with the driver. Since mp3 is not open-format, you need non-free codecs in order to read mp3 files (and some others). To install a host of useful, non-free stuff, sudo apt-get ubuntu-restricted-extras should work. If not, you can always install ubuntu-restricted-extras via the Software Center: the apt-get command is the command line, the Software Center does the same thing, but with a graphic user interface (GUI). Give that a try and then see if you still have sound problems.

---

### Post by BillyBoa on 2011-11-15
Well searching the results of the Synaptic installation I see that you have problem with the package hdjmod-dkms 

Just remove it

```
sudo apt-get remove hdjmod-dkms
```

---

### Post by BillyBoa on 2011-11-15
And about the other package hdjcpl try the same.

```
sudo apt-get remove hdjcpl
```

These are the drivers you tried to install

---

