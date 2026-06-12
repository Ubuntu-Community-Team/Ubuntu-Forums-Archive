---
title: "Can't update in 10.04"
date: 2010-09-17
forum: General Help
---

### Post by jarrod831 on 2010-09-17
It started when I was trying to install Cairo-Dock through the terminal, following the directions from the page I was using.  (Currently don't have it, because I reset the computer.)  Never got it installed and kept getting an error that said something along the lines of "'sudo' is not known on line 40 in source list"

When I reset the computer I was told to update through the package manager and it gave me this error:

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 40 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/B]

And while writing this post I noticed that my power button at the top right corner of my screen is no longer there due to a glitch in the top bar, I'll attack a screen shot.  

Thanks for the help in advance.  I'd appreciate it if you could explain in simple terms, as this is my first time messing with linux, and I installed it yesterday as a dual boot with windows 7 on my HP Pavilion dv5 2035 through wubi.

screen shot: [http://ubuntuone.com/p/GTo/](http://ubuntuone.com/p/GTo/)

---

### Post by sikander3786 on 2010-09-17
Type

```

cat /etc/apt/sources.list

```

and post the output here. There is something in the line #40 which doesn't like. We'll later get on to that power button issue.

EDIT: What does that red button in the tray mean? Have you also got some broken packages on your system?

---

### Post by jarrod831 on 2010-09-17
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted

sudo apt-key adv --keyserver keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
sudo apt-get update
sudo apt-get install cairo-dock-plug-ins
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) lucid main ## Cairo-Dock-PPA
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) lucid main ## Cairo-Dock-PPA
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable

there's the output

---

### Post by sikander3786 on 2010-09-17
> sudo apt-key adv --keyserver keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
sudo apt-get update
sudo apt-get install cairo-dock-plug-ins

Delete these lines. Why did you add them here? You need to type them in the terminal. After deleting type

```

sudo apt-get update

```

What happens?

EDIT: To delete them type

```

sudo gedit /etc/apt/sources.list

```

---

### Post by jarrod831 on 2010-09-17
I posted those three lines because they were direct output from the code you told me to type in.

when I type in that second code to get the update I get

> E: Type 'sudo' is not known on line 40 in source list /etc/apt/sources.list


edit: sorry didn't see your edit, so that's before i deleted the lines.

after the deleting I got: 
> jarrod@ubuntu:~$ sudo apt-get update
Get:1 [http://repository.glx-dock.org](http://repository.glx-dock.org) lucid Release.gpg [198B]
Ign [http://repository.glx-dock.org/ubuntu/](http://repository.glx-dock.org/ubuntu/) lucid/cairo-dock Translation-en_US  
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US             
Get:4 [http://repository.glx-dock.org](http://repository.glx-dock.org) lucid Release [2,850B]                    
Ign [http://ppa.launchpad.net/bisgi/ppa/ubuntu/](http://ppa.launchpad.net/bisgi/ppa/ubuntu/) lucid/main Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_US   
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release.gpg [198B]              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]               
Get:10 [http://repository.glx-dock.org](http://repository.glx-dock.org) lucid/cairo-dock Packages [2,971B]       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release [42.6kB]               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Get:13 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg [836B]               
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_US     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [37.4kB]    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]                
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [2,432B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [70.6kB]        
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [2,526B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                        
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,876B]  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/universe Packages [32.9kB]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/main Packages [80.2kB]         
Get:23 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release [7,240B]                 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/multiverse Packages [605B]     
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/restricted Packages [14B]      
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [117kB]       
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [297kB]           
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [3,652B]    
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,270B]    
Get:30 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages [48.8kB]          
Fetched 954kB in 2s (351kB/s)                            
W: Failed to fetch [http://ppa.launchpad.net/bisgi/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/bisgi/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by jarrod831 on 2010-09-17
Also, the red circle with the white line at the top right telling me to update disappeared after I did that.  Does that mean it's fixed or what?

---

### Post by sikander3786 on 2010-09-17
Yes it means that the problem has been fixed. Now go to Software Center under Applications menu, search for Cairo Dock and install it. It is the easier way of installation if you don't prefer command line.

---

### Post by jarrod831 on 2010-09-17
awesome, now about the power button issue if you would be so kind?

---

### Post by sikander3786 on 2010-09-17
Oh I forgot. Sorry.

Type

```

killall gnome-panel

```

After the panels restart, is the issue sorted out?

---

### Post by jarrod831 on 2010-09-17
yay it's fixed!  Thank you!

---

### Post by sikander3786 on 2010-09-17
You are Welcome. Please mark this thread as solved by using the Thread Tools near the top of the page.

Nice Ubuntu-ing.

Regards.

---

