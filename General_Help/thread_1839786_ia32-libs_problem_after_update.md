---
title: "ia32-libs problem after update"
date: 2011-09-06
forum: General Help
---

### Post by n0c0d3 on 2011-09-06
Yesterday I did a regular update and there was just one update which, I know for sure, had 'video' in its name. Iit may have been video4linux, but I don;t know for sure. I wanted to install it, as I always do with updates, but there only seemed to be a partial upgrade possible, which I did (but shouldn't have). Then other packages were removed and added. Because I have no clue about all these packages, I just let it go, thinking that everything will be alright when it would finish. This didn't seem the case.

It turned out ia32-libs was removed as well, and, I suppose because of  that, Google-Earth, some parts of Wine, Acrobat Reader and the Flash plugin in FireFox and who knows what else, were also removed.

I tried to re-install ia32-libs, but in Synaptic, in the dependencies-tab of ia32-libs, I get a large list of dependencies that are conflicting. When I try to install it anyway I get an error that 'lib32v4l-0' (which is a32-bit ollection of video4linux support libraries) can't be installed (because I may not have the right repository in the repo-list, but I sincerely doubt that) and the installation was aborted.

Does anyone have an idea on how to either undo that last (partial) update, or how to install the right packages and libraries again, or any other possible solution? Nowhere in the histories of Synaptic or Software Center can I find what was installed or removed.

My computer is 64-bit with Xubuntu 11.04 on it.

---

### Post by DavidAames on 2011-09-07
I have the *exact* same problem, running Ubuntu 11.04 64 bit. Anyone a clue?

---

### Post by n0c0d3 on 2011-09-07
I hate to bump the topic, but please, does anyone have a clue? If I (and as I read above, not just me) can't solve this I/we would have to do a fresh install, which is no fun at all on a system in use for about a year...
I really wouldn't even know where to start looking, what to remove or reinstall to get this solved.

Please, please... Do I sound desperate enough? ;-)

---

### Post by DavidAames on 2011-09-08
Yes, same here. It is the exact same problem I am facing right now and it started after installing updates via the 'Update Manager' earlier this week.

For example I had to manually install Adobe Flash player after those updates. It was removed from the system! When I try to install Teamviewer I get the ia32-libs error.

---

### Post by n0c0d3 on 2011-09-08
@DavidAames,
Did you also get this 'partial upgrade' option when updating before the ia32-libs package (and other software) was removed from your system?

I can't re-install any of the removed stuff anymore, or it installs but just doesn't work. I'm facing a complete fresh installation of Xubuntu I'm afraid, as there doesn't seem to be anyone to be able to give some support, but still need to finish some stuff first and make an awful lots of back-ups. Next week I'll do it when I have time left I think. :-(

---

### Post by DavidAames on 2011-09-08
Well I think I had that option also, but to be honest I clicked next next next (yes I know) without really paying attention. 

It was morning at the office and there was no coffee yet and... ah well...

Anyway, it is kinda strange that we are the only 2 people with this issue as it seems? Or are we simply missing something here?

---

### Post by n0c0d3 on 2011-09-09
@DavidAames
Yes, I blame the coffee too. But I had too much of my home-brew nuclear-strength coffee already I think ;) 
But one thing I know for sure: I'll never opt-in for a partial upgrade again. I've had problems with it before when upgrading from 10.10 to 11.04 (it was not the ia32-libs problem though). Then I could solve it in the CLI with a manual upgrade as described here. It might help you, but I doubt it. It doesn't work for me now anyways:
[http://ubuntuforums.org/showpost.php?p=10715284&postcount=5](http://ubuntuforums.org/showpost.php?p=10715284&postcount=5)

Good luck!

---

### Post by Bodsda on 2011-09-09
Can you paste the output of the following commands
 
```

cat /etc/apt/sources.list

```
```

sudo apt-get update && sudo apt-get upgrade

```
 
Thanks,
Bodsda

---

### Post by n0c0d3 on 2011-09-09
Hi Bodsda,
Thanks for your reply
 
```

cat /etc/apt/sources.list

```gives:
```

bart@Xub64:~/Desktop$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Xubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse
deb http://archive.ubuntu.com/ubuntu natty-backports restricted main multiverse universe
# deb http://ftp.nl.debian.org/debian sid main
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
# deb http://repository.spotify.com stable non-free
# deb-src http://repository.spotify.com stable non-free

#deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/InRelease
#deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/Release.gpg

#deb-src http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/natty/InRelease
#deb http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu/dists/natty/Release.gpg


deb http://www.ksplice.com/apt natty ksplice
deb-src http://www.ksplice.com/apt natty ksplice


deb http://archive.getdeb.net/ubuntu natty-getdeb apps
deb-src http://archive.getdeb.net/ubuntu natty-getdeb apps



deb http://dl.google.com/linux/deb/ stable non-free
deb http://apt.wxwidgets.org/ natty-wx main
deb-src http://apt.wxwidgets.org/ natty-wx main

```
And
```

sudo apt-get update && sudo apt-get upgrade

```has following results:
```

bart@Xub64:~/Desktop$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for bart: 
Ign http://archive.canonical.com natty InRelease                               
Ign http://apt.wxwidgets.org natty-wx InRelease                                
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://apt.wxwidgets.org natty-wx Release.gpg                              
Hit http://archive.canonical.com natty Release                                 
Hit http://apt.wxwidgets.org natty-wx Release                                  
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Hit http://apt.wxwidgets.org natty-wx/main Sources                             
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://apt.wxwidgets.org natty-wx/main amd64 Packages                      
Ign http://apt.wxwidgets.org natty-wx/main TranslationIndex                    
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://archive.canonical.com natty/partner Translation-en                  
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://archive.canonical.com natty/partner Translation-nl                  
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://dl.google.com stable InRelease                                      
Ign http://apt.wxwidgets.org natty-wx/main Translation-en_US                   
Ign http://apt.wxwidgets.org natty-wx/main Translation-en                      
Ign http://apt.wxwidgets.org natty-wx/main Translation-nl                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://www.ksplice.com natty InRelease                                     
Hit http://www.ksplice.com natty/ksplice Sources                               
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://www.ksplice.com natty/ksplice amd64 Packages                        
Ign http://www.ksplice.com natty/ksplice TranslationIndex                      
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://archive.getdeb.net natty-getdeb InRelease                           
Ign http://ppa.launchpad.net natty/main Translation-en                         
Hit http://archive.getdeb.net natty-getdeb Release.gpg                         
Ign http://ppa.launchpad.net natty/main Translation-nl                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-nl                         
Hit http://packages.medibuntu.org natty InRelease                              
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Ign http://archive.ubuntu.com natty-security InRelease                         
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.ubuntu.com natty-backports InRelease                        
Hit http://archive.ubuntu.com natty Release.gpg                                
Ign http://extras.ubuntu.com natty/main Translation-nl                         
Hit http://archive.ubuntu.com natty-updates Release.gpg                        
Hit http://archive.ubuntu.com natty-security Release.gpg                       
Hit http://archive.getdeb.net natty-getdeb Release                             
Hit http://archive.ubuntu.com natty-backports Release.gpg            
Hit http://archive.ubuntu.com natty Release    
Hit http://archive.ubuntu.com natty-updates Release
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://archive.ubuntu.com natty-security Release                           
Hit http://packages.medibuntu.org natty/free amd64 Packages                    
Ign http://dl.google.com stable InRelease                                      
Hit http://packages.medibuntu.org natty/non-free amd64 Packages                
Hit http://archive.ubuntu.com natty-backports Release                          
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://archive.ubuntu.com natty/universe Sources                           
Hit http://archive.ubuntu.com natty/multiverse Sources                         
Hit http://archive.ubuntu.com natty/main amd64 Packages                        
Hit http://archive.ubuntu.com natty/restricted amd64 Packages                  
Hit http://archive.ubuntu.com natty/universe amd64 Packages                    
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages                  
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/restricted Sources                 
Hit http://archive.ubuntu.com natty-updates/universe Sources                   
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                 
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages                
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages          
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages            
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages          
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty-security/main Sources                      
Hit http://archive.ubuntu.com natty-security/restricted Sources                
Hit http://archive.ubuntu.com natty-security/universe Sources                  
Hit http://archive.ubuntu.com natty-security/multiverse Sources                
Hit http://archive.ubuntu.com natty-security/main amd64 Packages               
Hit http://archive.ubuntu.com natty-security/restricted amd64 Packages         
Hit http://archive.ubuntu.com natty-security/universe amd64 Packages           
Hit http://archive.ubuntu.com natty-security/multiverse amd64 Packages         
Ign http://archive.ubuntu.com natty-security/main TranslationIndex             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://www.ksplice.com natty/ksplice Translation-en_US                     
Ign http://www.ksplice.com natty/ksplice Translation-en                        
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Hit http://archive.ubuntu.com natty/main Translation-nl                        
Ign http://www.ksplice.com natty/ksplice Translation-nl                        
Hit http://archive.ubuntu.com natty-backports/restricted amd64 Packages        
Hit http://archive.ubuntu.com natty-backports/main amd64 Packages              
Hit http://archive.ubuntu.com natty-backports/multiverse amd64 Packages        
Hit http://archive.ubuntu.com natty-backports/universe amd64 Packages          
Ign http://archive.ubuntu.com natty-backports/main TranslationIndex            
Ign http://archive.ubuntu.com natty-backports/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/universe TranslationIndex        
Hit http://archive.ubuntu.com natty/multiverse Translation-nl                  
Hit http://archive.ubuntu.com natty/restricted Translation-nl                  
Hit http://archive.ubuntu.com natty/universe Translation-nl                    
Hit http://archive.getdeb.net natty-getdeb/apps Sources                        
Get:1 http://dl.google.com stable Release.gpg [189 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://archive.getdeb.net natty-getdeb/apps amd64 Packages                 
Ign http://archive.getdeb.net natty-getdeb/apps TranslationIndex               
Get:3 http://dl.google.com stable Release [2544 B]                             
Get:4 http://dl.google.com stable Release [1338 B]                             
Get:5 http://dl.google.com stable/non-free amd64 Packages [1025 B]             
Ign http://dl.google.com stable/non-free TranslationIndex                      
Get:6 http://dl.google.com stable/main amd64 Packages [469 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://archive.ubuntu.com natty/main Translation-en                        
Ign http://packages.medibuntu.org natty/free Translation-nl                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Ign http://packages.medibuntu.org natty/non-free Translation-nl                
Ign http://archive.getdeb.net natty-getdeb/apps Translation-en_US              
Ign http://archive.getdeb.net natty-getdeb/apps Translation-en               
Ign http://archive.getdeb.net natty-getdeb/apps Translation-nl
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-nl
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-nl
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://dl.google.com stable/non-free Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-nl
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-nl
Ign http://dl.google.com stable/non-free Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-nl
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-nl
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-nl
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://dl.google.com stable/non-free Translation-nl
Ign http://archive.ubuntu.com natty-security/universe Translation-nl
Ign http://archive.ubuntu.com natty-backports/main Translation-en_US
Ign http://archive.ubuntu.com natty-backports/main Translation-en
Ign http://archive.ubuntu.com natty-backports/main Translation-nl
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_US
Ign http://dl.google.com stable/main Translation-en_US
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-nl
Ign http://dl.google.com stable/main Translation-en
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://archive.ubuntu.com natty-backports/restricted Translation-nl
Ign http://dl.google.com stable/main Translation-nl
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com natty-backports/universe Translation-en
Ign http://archive.ubuntu.com natty-backports/universe Translation-nl
Fetched 5763 B in 2min 36s (37 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Is there anything out of the order? I haven't added or removed repo's for quite some time and didn't have any problems until a few days ago, but maybe you see more than I do.

Bart

---

### Post by tenbeers on 2011-09-22
Hi there, any news or updates on this problem, because I have the same situation and tried everything I know, but with no success so far

---

### Post by DavidAames on 2011-09-22
I still have the same problem, am thinking about reinstalling Ubuntu .... :mad:

---

### Post by tenbeers on 2011-09-22
Hi David, may be I'm going to reinstall too, because flash plug-in, skype, teamviewer use this ia32-libs and I'm working with them every day. David, what do you think about new installation, would it be Natty again or Oneric?

---

### Post by n0c0d3 on 2011-09-22
I'm waiting with a re-install. In about 3 weeks 11.10 (Oneiric Ocelot) will be released into the wild. I hope this upgrade will solve the problem, but deep inside something tells me it won't. I hate those voices deep inside me ;)
If the upgrade won't solve the problem I will re-install Oneiric.

---

### Post by tenbeers on 2011-09-23
Hi again,
David and n0c0d3 - what worked for me:
1. I installed flash plug-in version 11 from adobe.com - you will see it
2. Update apt
3. ALT+F2 and type there "update-manager -d" without quotes
This will call Update manager and will show on the top upgrade to Oneiric
4. Upgraded my distro to 11.10 Oneiric
5. in terminal "sudo apt-get update" w/o quotes
6. in terminal "sudo apt-get install python"
7. started skype*.deb downloaded from their site, but this gave some error 
8. in terminal "echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
foreign-architecture i386"
9. in terminal "sudo apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386"
10. in terminal "sudo apt-get install libqtgui4:i386" 
11. started skype with no problem
I'm not sure this will work on your systems because my system and yours can have some differences, but you can try it
Cheers  ;)
Mike

---

### Post by n0c0d3 on 2011-09-23
Thanks for your advice teenbeers.

I already installed Flash 64 bit (all you need to do is copy libflashplayer.so from the download-file to /usr/lib/mozilla/plugins, if you use FF or course). I don't use Skype, but Google Earth and Adobe Reader still need the 32 bit libraries.
So the best solution would still be to get the ia32-libs package to work again. I'm not going to upgrade to 11.10 yet, I'll wait for the final Release. There are already troubles enough, so no Beta for me now ;)

Bart

---

### Post by n0c0d3 on 2011-10-14
Just to let you know, I upgraded to 11.10 and the ia32-libs were installed again. I had to do nothing extra for that. I re-installed most of the previously lost apps again and they installed without problems an work fine so far.

---

