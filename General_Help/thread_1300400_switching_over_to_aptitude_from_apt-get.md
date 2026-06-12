---
title: "switching over to aptitude from apt-get"
date: 2009-10-24
forum: General Help
---

### Post by iMisspell on 2009-10-24
While reading about 'aptitude' and 'apt-get' installs i seen a command to run for a person who has used apt-get for a period of time to "log" those installs "under" aptitude if they want to start using aptitude, but i cant find the article again.

I have a desktop which ive been using for some months now and used apt-get for just abuot all the installs (Synaptic a few times) and i would like to start to use aptitude.

any know this command or info abuot this ?

[edit]
[http://ubuntuforums.org/showpost.php?p=8162727&postcount=8](http://ubuntuforums.org/showpost.php?p=8162727&postcount=8)
_

---

### Post by Bachstelze on 2009-10-24
There is nothing particular to do. All package managers use the same database in the backend, so the packages you installed via apt-get or Synaptic will also appear as installed in Aptitude.

---

### Post by iMisspell on 2009-10-25
hummm... i thought what i read said something about the removal process. 
If a program was installed with api-get, aptitude would not remove it the same way as if aptitude was the original installer. 
By running "this command" it would change that, something with the dependences.

Its not that big of a deal, i just want to know (i like details) :)
The current machine ive been using is hosted on vmware, gonna be picking up another harddrive in the next week and have ubuntu running native in a dual bout with xp.

Gonna have to search and see if i can find the article and post it here.

_

---

### Post by rockstarrem on 2009-10-25
Don't mean to go off topic, but what are the differences between aptitude, apt-get, and synaptic? Particularly aptitude and apt-get, I see no difference.

---

### Post by iMisspell on 2009-10-25
Being new to linux, i could not even begin to explain :)
[http://www.google.com/search?q=differences+between+aptitude%2C+apt-get](http://www.google.com/search?q=differences+between+aptitude%2C+apt-get)

After reading abuot the two, i ran a few install tests and it seamed that aptitude would find more dependences to install and also list off current ones on my system which where no longer used and would remove then... simulare to apt-get prune (??? i think)

Theres links apon links talking abuot the difference between the two along with the same amount of opinions of which is better.

_

---

### Post by infinitejones on 2009-10-25
You might be thinking of 
```
aptitude purge
``` which, according to the aptitude help screen (aptitude --help) "removes packages and their configuration files".

There's also ```
sudo apt-get autoremove
``` which is very useful for uninstalling dependencies and libraries that were needed to install a specific application, and are no longer needed after uninstalling it ("orphan" dependencies).

For example, if you install Banshee music player, it will also install a lot of Mono libraries (if they're not there already). If you then decide to uninstall Banshee, a simple ```
sudo apt-get remove banshee
``` will not automatically remove the Mono libraries.

It's not the end of the world if you don't remove them, but if you wanted to, you could then do ```
sudo apt-get autoremove
```

---

### Post by cilynx on 2009-10-25
As the OP is hinting at, aptitude remembers more stuff about what's been done.  If you install a program with aptitude and said program has some dependencies that get installed along with it, aptitude will remember that and remove the dependencies as well when the main application is removed.  As for a command to update whatever database manages that with the current state of the system, I dunno.

---

### Post by QLee on 2009-10-25
> **iMisspell said:**
> hummm... i thought what i read said something about the removal process. 
If a program was installed with api-get, aptitude would not remove it the same way as if aptitude was the original installer. 
By running "this command" it would change that, something with the dependences.

Its not that big of a deal, i just want to know (i like details) :)
The current machine ive been using is hosted on vmware, gonna be picking up another harddrive in the next week and have ubuntu running native in a dual bout with xp.

Gonna have to search and see if i can find the article and post it here.

_

I think I have an idea of what you're meaning. When Debian first made Aptitude the recommended package manager, people who had been using apt-get usually needed to run "aptitude keep-all" the first time they used Aptitude to avoid a situation where some packages they wanted to keep were being un-installed. IIRC, that had to be done too if apt-get was used and then aptitude was used again. This was at least a couple of years ago, there would be several documents on the 'Net about it, I have no idea what the current state about the issue is, but the important thing to take away from this discussion is that, whichever method of package management you use, investigate what it is proposing to do before you click or hit enter.

---

### Post by mcduck on 2009-10-25
> **cilynx said:**
> As the OP is hinting at, aptitude remembers more stuff about what's been done.  If you install a program with aptitude and said program has some dependencies that get installed along with it, aptitude will remember that and remove the dependencies as well when the main application is removed.  As for a command to update whatever database manages that with the current state of the system, I dunno.

The difference is pretty much history, since apt-get is also able to remove the dependencies, has been for couple of years now. Most articles that discuss the difference between aptitude and apt-get are quite old, dating back to time before this feature was added to apt-get.

Also the reason why aptitude seems to find more dependencies when installing something is that it, by default, also installs all recommended packages instead of just the dependencies.

(personally, I prefer apt-get since aptitude sometimes tries to be "too smart" and ends doing rather stupid things while apt-get just does what it's told to do.)

---

### Post by lovinglinux on 2009-10-25
> **mcduck said:**
> Also the reason why aptitude seems to find more dependencies when installing something is that it, by default, also installs all recommended packages instead of just the dependencies.


I guess apt-get also installs recommends by default since Jaunty. Anyways, this is the default behavior in Karmic.

---

### Post by iMisspell on 2009-10-25
> **QLee said:**
> ...When Debian first made Aptitude the recommended package manager, people who had been using apt-get usually needed to run "**aptitude keep-all**" the first time they used Aptitude to avoid a situation where some packages they wanted to keep were being un-installed...
Thats it ( aptitude keep-all ) ...
Aside from the info here in this thread, heres two other threads with a "deep" discussion about apt-get and aptitude for anyone who is interested (still can not find the article about 'aptitude keep-all', but thats it, thanks, QLee ).

apt-get and aptitude on the 'sidux' branch of Debian.
[http://sidux.com/PNphpBB2-viewtopic-t-16808.html](http://sidux.com/PNphpBB2-viewtopic-t-16808.html)

and...
[http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/](http://www.linuxquestions.org/questions/debian-26/apt-get-vs.-aptitude-363365/)


[edit]
> **mcduck said:**
> Also the reason why aptitude seems to find more dependencies when installing something is that it, by default, also installs all recommended packages instead of just the dependencies.
Aside from the use of the extra space which they will be taking up, is it really that bad of an idea to install the "suggested" dependencies ?
If a person wanted to, would it be better to create an "install script" which would check and compair what the two installers wanted to install and then make a choice from there ? And if the person mainly installs with aptitude, but chooses to use apt-get from time to time, to run 'aptitude keep-all' after the use of apt-get ?



_

---

### Post by mcduck on 2009-10-25
> **lovinglinux said:**
> I guess apt-get also installs recommends by default since Jaunty. Anyways, this is the default behavior in Karmic.

Is it? I just installed couple of packages with apt-get (in Karmic) and it didn't automatically install any of the recommended packages. (Which was just fine for me, since I didn't need or want any of them anyway...)

---

### Post by raptir on 2009-10-25
I use both Aptitude and apt-get when I'm using a debian-based distribution. I love aptitude's GUI option for searching packages, but I also like apt-get's autoremove. There's really no reason to pick one or the other.

---

### Post by lovinglinux on 2009-10-25
> **mcduck said:**
> Is it? I just installed couple of packages with apt-get (in Karmic) and it didn't automatically install any of the recommended packages. (Which was just fine for me, since I didn't need or want any of them anyway...)

See posts 8, 9 and 10 of [http://ubuntuforums.org/showthread.php?t=1296955](http://ubuntuforums.org/showthread.php?t=1296955)

---

### Post by mcduck on 2009-10-26
> **lovinglinux said:**
> See posts 8, 9 and 10 of [http://ubuntuforums.org/showthread.php?t=1296955](http://ubuntuforums.org/showthread.php?t=1296955)

Yes, I have seen posts about it, but I thought that they didn't actually change the behavior since, like I said, it definitely didn't install recommended packages automatically when I tried.

edit: I suppose they must have been suggested packages then, not recommended. That would explain it...

---

### Post by lovinglinux on 2009-10-26
> **mcduck said:**
> Yes, I have seen posts about it, but I thought that they didn't actually change the behavior since, like I said, it definitely didn't install recommended packages automatically when I tried.

edit: I suppose they must have been suggested packages then, not recommended. That would explain it...

The default behavior:

**Command:** *sudo apt-get --simulate install screenlets*

                       
```
Reading package lists... Done                            
Building dependency tree                                 
Reading state information... Done                        
**The following extra packages will be installed: **         
  alacarte capplets-data desktop-file-utils evolution-data-server evolution-data-server-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-media gnome-media-common gnome-menus gnome-panel gnome-panel-data gnome-session gnome-session-bin gnome-settings-daemon gnome-system-monitor gnome-user-guide indicator-applet indicator-messages libatspi1.0-0 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libdbusmenu-glib0 libdbusmenu-gtk0 libdevkit-power-gobject1 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libgdata-google1.2-1 libgdata1.2-1 libgnome-desktop-2-11 libgnome-media0 libgnome-menu2 libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgucharmap7 libgweather-common libgweather1 libmetacity0 libpanel-applet2-0 libpulse-mainloop-glib0 libtidy-0.99-0 libunique-1.0-0 metacity metacity-common mousetweaks nautilus nautilus-data python-chardet python-evolution python-feedparser python-gmenu python-gnomeapplet python-gnomekeyring python-gtkmozembed python-rsvg python-utidylib python-wnck screen-resolution-extra ubuntu-system-service                                   
**Suggested packages:**
  evolution evolution-data-server-dbg acpid tomboy gnome-netstatus-applet deskbar-applet cpufrequtils gnome-screensaver xscreensaver gnome2-user-guide gnome-system-tools epiphany-browser menu-xdg desktop-base eog gnome-app-install brasero nautilus-cd-burner gnome-orca xfconf
**The following NEW packages will be installed: **
  alacarte capplets-data desktop-file-utils evolution-data-server evolution-data-server-common gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-media gnome-media-common gnome-menus gnome-panel gnome-panel-data gnome-session gnome-session-bin gnome-settings-daemon gnome-system-monitor gnome-user-guide indicator-applet indicator-messages libatspi1.0-0 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libdbusmenu-glib0 libdbusmenu-gtk0 libdevkit-power-gobject1 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libgdata-google1.2-1 libgdata1.2-1 libgnome-desktop-2-11 libgnome-media0 libgnome-menu2 libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgucharmap7 libgweather-common libgweather1 libmetacity0 libpanel-applet2-0 libpulse-mainloop-glib0 libtidy-0.99-0 libunique-1.0-0 metacity metacity-common mousetweaks nautilus nautilus-data python-chardet python-evolution python-feedparser python-gmenu python-gnomeapplet python-gnomekeyring python-gtkmozembed python-rsvg python-utidylib python-wnck screen-resolution-extra screenlets ubuntu-system-service                        
**0 upgraded, 72 newly installed, 0 to remove and 0 not upgraded. **
Inst libgnome-desktop-2-11 (1:2.28.1-0ubuntu2 Ubuntu:9.10/karmic)      
Inst libgnomekbd-common (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)   
Inst libgnomekbd4 (2.28.0-0ubuntu2 Ubuntu:9.10/karmic) 
Inst libgnomekbdui4 (2.28.0-0ubuntu2 Ubuntu:9.10/karmic) 
Inst libgucharmap7 (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)   
Inst libgweather-common (2.28.0-1ubuntu2 Ubuntu:9.10/karmic)
Inst libgweather1 (2.28.0-1ubuntu2 Ubuntu:9.10/karmic)   
Inst libpanel-applet2-0 (1:2.28.0-0ubuntu6 Ubuntu:9.10/karmic) 
Inst gnome-applets-data (2.28.0-0ubuntu2 Ubuntu:9.10/karmic) 
Inst libedataserver1.2-11 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)  
Inst libecal1.2-7 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)    
Inst libcamel1.2-14 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst libebook1.2-9 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic) 
Inst evolution-data-server-common (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst libedataserverui1.2-8 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)       
Inst libgnome-menu2 (2.28.0.1-0ubuntu1 Ubuntu:9.10/karmic)     
Inst gnome-panel-data (1:2.28.0-0ubuntu6 Ubuntu:9.10/karmic)
Inst gnome-desktop-data (1:2.28.1-0ubuntu2 Ubuntu:9.10/karmic)  
Inst libcanberra-gtk0 (0.15-0ubuntu7 Ubuntu:9.10/karmic)        
Inst libgnome-window-settings1 (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)       
Inst metacity-common (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)                         
Inst libmetacity0 (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)    
Inst libunique-1.0-0 (1.1.2-1ubuntu1 Ubuntu:9.10/karmic)  
Inst capplets-data (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)     
Inst libpulse-mainloop-glib0 (1:0.9.19-0ubuntu3 Ubuntu:9.10/karmic)      
Inst gnome-settings-daemon (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)    
Inst python-gmenu (2.28.0.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst gnome-menus (2.28.0.1-0ubuntu1 Ubuntu:9.10/karmic)   
Inst desktop-file-utils (0.15-2ubuntu1 Ubuntu:9.10/karmic)  
Inst ubuntu-system-service (0.1.16 Ubuntu:9.10/karmic)    
Inst gnome-control-center (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)    
Inst gnome-about (1:2.28.1-0ubuntu2 Ubuntu:9.10/karmic) 
Inst gnome-panel (1:2.28.0-0ubuntu6 Ubuntu:9.10/karmic)   
Inst gnome-applets (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)        
Inst alacarte (0.12.4-0ubuntu2 Ubuntu:9.10/karmic)      
Inst libebackend1.2-0 (2.28.1-0ubuntu1                                                              
Inst libedata-book1.2-2 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)    
Inst libedata-cal1.2-6 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)     
Inst libegroupwise1.2-13 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)         
Inst libgdata1.2-1 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)            
Inst libgdata-google1.2-1 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)   
Inst evolution-data-server (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)    
Inst gnome-media-common (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst libgnome-media0 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)   
Inst gnome-media (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)    
Inst nautilus-data (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst nautilus (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst metacity (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)     
Inst libdevkit-power-gobject1 (011-1ubuntu1 Ubuntu:9.10/karmic)  
Inst gnome-session-bin (2.28.0-0ubuntu5 Ubuntu:9.10/karmic)   
Inst gnome-session (2.28.0-0ubuntu5 Ubuntu:9.10/karmic) 
Inst gnome-system-monitor (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)     
Inst gnome-user-guide (2.28.0+git20090921ubuntu2 Ubuntu:9.10/karmic)      
Inst libdbusmenu-glib0 (0.1.6-0ubuntu1 Ubuntu:9.10/karmic)     
Inst libdbusmenu-gtk0 (0.1.6-0ubuntu1 Ubuntu:9.10/karmic)       
Inst indicator-messages (0.2.6-0ubuntu1 Ubuntu:9.10/karmic)  
Inst libatspi1.0-0 (1.28.1-0ubuntu1 Ubuntu:9.10/karmic)      
Inst libcanberra-gtk-module (0.15-0ubuntu7 Ubuntu:9.10/karmic)  
Inst libtidy-0.99-0 (20081224cvs-1 Ubuntu:9.10/karmic)  
Inst mousetweaks (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)     
Inst python-chardet (1.0.1-1.1 Ubuntu:9.10/karmic)   
Inst python-evolution (2.28.0-0ubuntu1 Ubuntu:9.10/karmic) 
Inst python-feedparser (4.1-14 Ubuntu:9.10/karmic)       
Inst python-gnomeapplet (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)     
Inst python-gnomekeyring (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)          
Inst python-gtkmozembed (2.25.3-3ubuntu1 Ubuntu:9.10/karmic)        
Inst python-rsvg (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)    
Inst python-utidylib (0.2-3.2ubuntu1 Ubuntu:9.10/karmic)        
Inst python-wnck (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)         
Inst screen-resolution-extra (0.11 Ubuntu:9.10/karmic)             
Inst screenlets (0.1.2-7 Ubuntu:9.10/karmic)         
Conf libgnome-desktop-2-11 (1:2.28.1-0ubuntu2 Ubuntu:9.10/karmic)               
Conf libgnomekbd-common (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)      
Conf libgnomekbd4 (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)           
Conf libgnomekbdui4 (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)                 
Conf libgucharmap7 (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)         
Conf libgweather-common (2.28.0-1ubuntu2 Ubuntu:9.10/karmic)                
Conf libgweather1 (2.28.0-1ubuntu2 Ubuntu:9.10/karmic)                   
Conf libpanel-applet2-0 (1:2.28.0-0ubuntu6 Ubuntu:9.10/karmic)                         
Conf gnome-applets-data (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)              
Conf libedataserver1.2-11 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)              
Conf libecal1.2-7 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)                
Conf libcamel1.2-14 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)                 
Conf libebook1.2-9 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)          
Conf evolution-data-server-common (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)               
Conf libedataserverui1.2-8 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)              
Conf libgnome-menu2 (2.28.0.1-0ubuntu1 Ubuntu:9.10/karmic)               
Conf gnome-panel-data (1:2.28.0-0ubuntu6 Ubuntu:9.10/karmic)   
Conf gnome-desktop-data (1:2.28.1-0ubuntu2 Ubuntu:9.10/karmic)        
Conf libcanberra-gtk0 (0.15-0ubuntu7 Ubuntu:9.10/karmic)   
Conf libgnome-window-settings1 (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)         
Conf metacity-common (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)                
Conf libmetacity0 (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)      
Conf libunique-1.0-0 (1.1.2-1ubuntu1 Ubuntu:9.10/karmic)     
Conf libpulse-mainloop-glib0 (1:0.9.19-0ubuntu3 Ubuntu:9.10/karmic)        
Conf gnome-settings-daemon (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)        
Conf python-gmenu (2.28.0.1-0ubuntu1 Ubuntu:9.10/karmic)    
Conf gnome-menus (2.28.0.1-0ubuntu1 Ubuntu:9.10/karmic)         
Conf desktop-file-utils (0.15-2ubuntu1 Ubuntu:9.10/karmic)     
Conf ubuntu-system-service (0.1.16 Ubuntu:9.10/karmic)            
Conf gnome-control-center (1:2.28.1-0ubuntu1                                              
Conf gnome-about (1:2.28.1-0ubuntu2 Ubuntu:9.10/karmic)      
Conf gnome-panel (1:2.28.0-0ubuntu6 Ubuntu:9.10/karmic)          
Conf gnome-applets (2.28.0-0ubuntu2 Ubuntu:9.10/karmic)         
Conf alacarte (0.12.4-0ubuntu2 Ubuntu:9.10/karmic)           
Conf libebackend1.2-0 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)                 
Conf libedata-book1.2-2 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)       
Conf libedata-cal1.2-6 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf libegroupwise1.2-13 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf libgdata1.2-1 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf libgdata-google1.2-1 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf evolution-data-server (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf gnome-media-common (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf libgnome-media0 (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf gnome-media (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf nautilus-data (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf nautilus (1:2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf metacity (1:2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf libdevkit-power-gobject1 (011-1ubuntu1 Ubuntu:9.10/karmic)
Conf gnome-session-bin (2.28.0-0ubuntu5 Ubuntu:9.10/karmic)
Conf gnome-session (2.28.0-0ubuntu5 Ubuntu:9.10/karmic)
Conf gnome-system-monitor (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf gnome-user-guide (2.28.0+git20090921ubuntu2 Ubuntu:9.10/karmic)
Conf libdbusmenu-glib0 (0.1.6-0ubuntu1 Ubuntu:9.10/karmic)
Conf libdbusmenu-gtk0 (0.1.6-0ubuntu1 Ubuntu:9.10/karmic)
Conf indicator-applet (0.2.0-0ubuntu2 Ubuntu:9.10/karmic)
Conf indicator-messages (0.2.6-0ubuntu1 Ubuntu:9.10/karmic)
Conf libatspi1.0-0 (1.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf libcanberra-gtk-module (0.15-0ubuntu7 Ubuntu:9.10/karmic)
Conf libtidy-0.99-0 (20081224cvs-1 Ubuntu:9.10/karmic)
Conf mousetweaks (2.28.1-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-chardet (1.0.1-1.1 Ubuntu:9.10/karmic)
Conf python-evolution (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-feedparser (4.1-14 Ubuntu:9.10/karmic)
Conf python-gnomeapplet (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-gnomekeyring (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-gtkmozembed (2.25.3-3ubuntu1 Ubuntu:9.10/karmic)
Conf python-rsvg (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-utidylib (0.2-3.2ubuntu1 Ubuntu:9.10/karmic)
Conf python-wnck (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf screen-resolution-extra (0.11 Ubuntu:9.10/karmic)
Conf screenlets (0.1.2-7 Ubuntu:9.10/karmic)
```


Without recommends:

**Command:** *sudo apt-get --simulate install screenlets --no-install-recommends*

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
**The following extra packages will be installed:**
  python-rsvg python-wnck
**Suggested packages:**
  evolution tomboy gnome-orca xfconf
**Recommended packages:**
  python-feedparser python-gmenu python-gtkmozembed python-gnome2-extras python-evolution python-gnome2-desktop metacity
  xcompmgr compiz xfwm4
**The following NEW packages will be installed:**
  python-rsvg python-wnck screenlets
**0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.**
Inst python-rsvg (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Inst python-wnck (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Inst screenlets (0.1.2-7 Ubuntu:9.10/karmic)
Conf python-rsvg (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf python-wnck (2.28.0-0ubuntu1 Ubuntu:9.10/karmic)
Conf screenlets (0.1.2-7 Ubuntu:9.10/karmic)
```

---

