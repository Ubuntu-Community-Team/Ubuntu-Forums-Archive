---
title: "libgl-mesa broken packages after installing 11.10"
date: 2011-11-01
forum: General Help
---

### Post by hobbleDHoy on 2011-11-01
After I upgraded to 11.10, whenever I do "apt-get upgrade" or "apt-get dist-upgrade" I get the following message:

```

The following packages have been kept back:
  libgl1-mesa-dri libgl1-mesa-glx xserver-xorg-core

```

I need libgl-mesa in order to build several projects, and I seem unable to install it. I've tried "apt-get install -f", "apt-get clean" and pretty much every trick in apt-get and synaptic I can think of, and no progress has been made. Does anyone know what I can do?

---

### Post by mc4man on 2011-11-01
What is the reported reason why those packages will not upgrade, apt-get or synaptic should say why.

What are the current versions of those 3 packages (look in synaptic

---

### Post by hobbleDHoy on 2011-11-01
"apt-get upgrade" tells me nothing, but if I try to apt-get install any of the mentioned packages, I get the following:

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri : Breaks: libgl1-mesa-glx (< 7.10.3-0ubuntu1) but 7.10.2-0ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.


```

libgl1-mesa-dri and libgl1-mesa-glx are version 7.10.2-0ubuntu2, xserver-xorg-core is version 2:1.10.1-1ubuntu1.2.

---

### Post by mc4man on 2011-11-01
The current versions are 7.11-0ubuntu3 for mesa & 2:1.10.4-1ubuntu4.1 for xorg, what you have aren't even the latest natty versions (7.10.2-0ubuntu2.1 for mesa

So it would seem your 'upgrade' wasn't that successful.

What does this show?

sudo apt-get update

---

### Post by hobbleDHoy on 2011-11-01
It lists all of the mirrors, and then "Fetched 602 kB in 1s (361 kB/s)                                          
Reading package lists... Done". Do you want me to post the entire output?

---

### Post by mc4man on 2011-11-01
Did it show using oneiric sources or natty sources? I guess you could post the results or the contents of your /etc/apt/sources.list

---

### Post by hobbleDHoy on 2011-11-01
Ok, here's my sources.list:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe

---

### Post by mc4man on 2011-11-01
Other than the partners on natty the list looks fine. (& you have proposed enabled - not always the best idea to upgrade  all the proposed, but not a factor here.

So if you where to open synaptic, click on reload, then search for instance xserver-xorg-core, it should show an upgrade to 2:1.10.4-1ubuntu4.2 as being available. Does it & if so will it let you do so?

---

### Post by hobbleDHoy on 2011-11-01
They show up as having updates available, but instead of check-boxes there are exclamation-marks. It lets me do "mark for upgrade", but if I do that, it tells me about the same broken dependencies.

---

### Post by mc4man on 2011-11-01
Not sure - maybe if you can install aptitude it will provide some answers
(Do you have any mesa or xserver-xorg dev packages installed?, if so try removing them & see if it helps

Haven't used aptitude in quite a while (aptitude help will show commands

Maybe start with 
sudo aptitude update && sudo aptitude safe-upgrade 
then see what  this shows 
sudo aptitude full-upgrade

---

### Post by hobbleDHoy on 2011-11-02
I tried to install them via aptitude, and I didn't pay enough attention when I did it, and so it removed my entire ubuntu-desktop :P I have got it back up now, but so are also the old libraries, which are again impossible to upgrade:p This is really weird and frustrating, is the only way out a reinstall?

---

### Post by Username12345 on 2011-11-09
I have this exact same error. When I try 'sudo aptitude full-upgrade' it comes up with:

The following packages have unmet dependencies:
  libgl1-mesa-glx: Depends: libglapi-mesa (= 7.11-0ubuntu3) but 7.12.0~git20111003.1165b64f-0ubuntu0sarvatt~natty is installed.
The following actions will resolve these dependencies:

       Remove the following packages:                                           
1)       brasero                                                                
2)       cheese                                                                 
3)       compiz                                                                 
4)       compiz-gnome                                                           
5)       compiz-plugins                                                         
6)       compiz-plugins-default                                                 
7)       compiz-plugins-main                                                    
8)       compiz-plugins-main-default                                            
9)       eog                                                                    
10)      evolution                                                              
11)      evolution-exchange                                                     
12)      evolution-plugins                                                      
13)      freeglut3                                                              
14)      gdm                                                                    
15)      gdm-guest-session                                                      
16)      gnome-applets                                                          
17)      gnome-control-center                                                   
18)      gnome-media                                                            
19)      gnome-panel                                                            
20)      gnome-screensaver                                                      
21)      gnome-session                                                          
22)      gnome-session-bin                                                      
23)      gnome-session-fallback                                                 
24)      gnome-settings-daemon                                                  
25)      gvfs                                                                   
26)      gvfs-backends                                                          
27)      gvfs-bin                                                               
28)      gvfs-fuse                                                              
29)      indicator-datetime                                                     
30)      indicator-power                                                        
31)      indicator-session                                                      
32)      libevolution                                                           
33)      libgl1-mesa-glx                                                        
34)      libgle3                                                                
35)      libglew1.5                                                             
36)      libglewmx1.5                                                           
37)      libglu1-mesa                                                           
38)      libgnome-desktop-3-2                                                   
39)      libnux-1.0-0                                                           
40)      libqt4-opengl                                                          
41)      libunity-2d-private0                                                   
42)      libunity-core-4.0-4                                                    
43)      libvisual-0.4-plugins                                                  
44)      mesa-utils                                                             
45)      nautilus                                                               
46)      nautilus-sendto                                                        
47)      nautilus-share                                                         
48)      nux-tools                                                              
49)      python-opengl                                                          
50)      ubuntu-desktop                                                         
51)      ubuntu-tweak                                                           
52)      ubuntuone-client-gnome                                                 
53)      unity                                                                  
54)      unity-2d                                                               
55)      unity-2d-launcher                                                      
56)      unity-2d-panel                                                         
57)      unity-2d-places                                                        
58)      unity-2d-spread                                                        
59)      wine1.3                                                                
60)      x11-utils                                                              
61)      xorg                                                                   

       Leave the following dependencies unresolved:                             
62)      banshee recommends brasero                                             
63)      evolution-common recommends evolution                                  
64)      gcalctool recommends gvfs                                              
65)      gnome-terminal recommends gvfs                                         
66)      indicator-appmenu recommends indicator-applet | indicator-renderer     
67)      indicator-messages recommends indicator-applet | indicator-renderer    
68)      libgnome2-0 recommends gvfs                                            
69)      libvisual-0.4-0 recommends libvisual-0.4-plugins                       
70)      mousetweaks recommends gnome-control-center                            
71)      vino recommends gvfs                                                   
72)      xdg-utils recommends x11-utils                                         
73)      xterm recommends x11-utils                                             
74)      alacarte recommends gnome-panel                                        
75)      cheese recommends gvfs                                                 
76)      compizconfig-settings-manager recommends compiz-plugins                
77)      compizconfig-settings-manager recommends compiz-plugins-main           
78)      gnome-applets recommends gnome-media                                   
79)      gnome-panel recommends gnome-applets                                   
80)      gnome-panel recommends gnome-session (>= 2.26)                         
81)      gnome-panel recommends gnome-settings-daemon                           
82)      gnome-panel recommends gvfs                                            
83)      gnome-panel-data recommends gnome-panel                                
84)      pcmanfm recommends gvfs-backends                                       
85)      pcmanfm recommends gvfs-fuse                                           
86)      winetricks recommends wine1.3 | wine1.2 | cxoffice5 | cxgames5         
87)      wine1.3-gecko recommends wine1.3                                       
88)      compiz-core recommends compiz-plugins-default (= 1:0.9.6+bzr20110929-0u
89)      empathy recommends gvfs-backends                                       
90)      evince recommends gvfs                                                 
91)      file-roller recommends gvfs                                            
92)      gnome-bluetooth recommends gvfs-backends                               
93)      gnome-control-center recommends gnome-session                          
94)      gnome-control-center-data recommends gnome-control-center (>= 1:3.2.1-0
95)      gnome-games-common recommends gvfs                                     
96)      gnome-online-accounts recommends gnome-control-center                  
97)      gnome-screenshot recommends nautilus                                   
98)      gnome-system-monitor recommends gvfs                                   
99)      nautilus recommends gvfs-backends                                      
100)     nautilus-sendto-empathy recommends nautilus-sendto (>= 2.28.2-2)       
101)     totem-plugins recommends gnome-settings-daemon                         
102)     unity recommends indicator-datetime                                    
103)     unity recommends indicator-power                                       
104)     unity recommends indicator-session                    

Should I complete it?

---

### Post by Netich on 2011-11-16
i have this exact problem. I have just upgraded from natty. my sources are all oneiric, and forcing to upgrade these 3 packages would seem to uninstall ubuntu-desktop.

Anyway, the system seems to work fine, but...

---

