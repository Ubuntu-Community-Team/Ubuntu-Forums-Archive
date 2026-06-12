---
title: "&quot;Major failure of your software management system&quot; Help!!"
date: 2009-08-29
forum: General Help
---

### Post by goseph on 2009-08-29
When I run Add/Remove programs I am informed:

```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```"sudo apt-get update" doesn't appear to do anything and "sudo apt-get install -f" prompts me to tell it what to do.

/etc/apt/sources.list is as follows:

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```

---

### Post by NoaHall on 2009-08-29
What do you mean doesn't appear to do anything? Post the output of apt-get update here.

---

### Post by goseph on 2009-08-29
Incidentally, this all happened straight after I attempted to install this .deb:
[http://gnofract4d.sourceforge.net/](http://gnofract4d.sourceforge.net/)

The Graphical package installer didn't have the install button highlighted and I had no idea why. I tried moving it from tmp to my home folder and then setting the permissions to 777 and still nothing. I speculate wildly that this is connected since permissions are mentioned in the above dramatic error message!

---

### Post by goseph on 2009-08-29
> **NoaHall said:**
> What do you mean doesn't appear to do anything? Post the output of apt-get update here.

Thanks for quick reply! I guess I just meant that it didn't solve the problem.

Output:

```

Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB    
Hit http://gb.archive.ubuntu.com jaunty Release.gpg                            
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB                 
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB           
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_GB              
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_GB                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_GB            
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Hit http://gb.archive.ubuntu.com jaunty-backports Release.gpg                  
Hit http://download.virtualbox.org jaunty Release.gpg                          
Ign http://download.virtualbox.org jaunty/non-free Translation-en_GB           
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://archive.canonical.com jaunty Release                                
Hit http://packages.medibuntu.org jaunty Release                               
Ign http://gb.archive.ubuntu.com jaunty-backports/main Translation-en_GB       
Ign http://gb.archive.ubuntu.com jaunty-backports/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com jaunty-backports/universe Translation-en_GB   
Hit http://download.virtualbox.org jaunty Release                              
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Ign http://gb.archive.ubuntu.com jaunty-backports/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com jaunty Release                                
Hit http://gb.archive.ubuntu.com jaunty-updates Release                        
Hit http://archive.canonical.com jaunty/partner Packages                       
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://download.virtualbox.org jaunty/non-free Packages                    
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://gb.archive.ubuntu.com jaunty-backports Release                      
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty/main Packages
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-backports/main Packages
Hit http://gb.archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-backports/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-backports/main Sources
Hit http://gb.archive.ubuntu.com jaunty-backports/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-backports/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-backports/multiverse Sources
Reading package lists... Done


```

---

### Post by NoaHall on 2009-08-29
You're quite a dramatic person. A actor perchance?

okay, now try accessing synaptic, and see what happens, and try accessing add/remove again

If that fails - run the deb again and see what happens. Then try "sudo apt-get update" and post the output here.

---

### Post by goseph on 2009-08-29
Upon attempting to reinstall the .deb I get:

"Your system has broken dependencies. This application cannot continue until this is fixed. To fix it run 'gksudo synaptic' or 'sudo apt-get install -f' in a terminal window.

"gksudo synaptic" gives:


"You have 1 broken package on your system!

Use the "Broken" filter to locate it."

I didn't know what that meant so I blindly clicked on: Edit => Fix broken packages and then Apply

and all was fixed automagically!!

Thankyou community!

---

### Post by uylug on 2009-08-29
open synaptic and click Edit -> Fix broken packages.

Lol, just seen your post.

---

### Post by goseph on 2009-08-29
The automagick process removed gnofractal_whatever.deb and I was able to go on my add/remove.. without threatening messages popping up.

I re-downloaded gnofractal_whatevr.deb and it still doesn't want to install though.. any thoughts?

---

### Post by goseph on 2009-08-29
> **NoaHall said:**
> You're quite a dramatic person. A actor perchance?

Just a student I'm afraid, I do like pantomimes though!!

---

### Post by NoaHall on 2009-08-29
Hm.. Try compiling it yourself? or maybe find a repository with it on.

---

