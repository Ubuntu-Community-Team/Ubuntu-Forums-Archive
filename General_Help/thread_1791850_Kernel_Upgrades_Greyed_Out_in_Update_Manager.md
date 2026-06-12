---
title: "Kernel Upgrades Greyed Out in Update Manager"
date: 2011-06-27
forum: General Help
---

### Post by fleamour on 2011-06-27
I am still running 10.10 & in no hurry to upgrade to Unity as prefer Cairo Dock (gotta love Linux for its customization!)  

When searching via update manager, I see new kernels listed under important security updates, but they are all greyed out & not selectable.

Should I worry?

---

### Post by snowpine on 2011-06-27
If you are comfortable using the Terminal you can try:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Copy & paste the output here and I'll take a look for you. :)

---

### Post by fleamour on 2011-06-27
Thanks!!!  Probably become a mess over time...

```
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/ maverick/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg                  
Hit http://security.ubuntu.com maverick-security Release                       
Get:1 http://dl.google.com stable Release.gpg [198B]                           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release                    
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources    
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages  
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/ maverick/main Translation-en
Hit http://gb.archive.ubuntu.com maverick-updates Release
Ign http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release                        
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://gb.archive.ubuntu.com maverick/main Sources                         
Hit http://gb.archive.ubuntu.com maverick/restricted Sources         
Hit http://gb.archive.ubuntu.com maverick/universe Sources           
Hit http://gb.archive.ubuntu.com maverick/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages         
Hit http://ppa.launchpad.net maverick Release                        
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages     
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages   
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources       
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources 
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://gb.archive.ubuntu.com maverick-updates/main i386 Packages 
Hit http://ppa.launchpad.net maverick Release                        
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get:2 http://dl.google.com stable Release [1,351B]
Get:3 http://dl.google.com stable/main i386 Packages [1,258B]
Fetched 2,807B in 5s (505B/s)
```

---

### Post by snowpine on 2011-06-27
I think something got cut off at the bottom... I don't see the output of "sudo apt-get dist-upgrade"?

---

### Post by fleamour on 2011-06-27
My bad!

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux linux-generic linux-headers-generic linux-image linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by fleamour on 2011-06-27
Have tidied/unticked some historically (since abandoned) entries.  Still greyed out.

---

### Post by snowpine on 2011-06-27
I'm not sure what to tell you; "dist-upgrade" has always worked well for me. Maybe go into Synaptic (gksu synaptic) and check whether those packages have a hold/lock at their current version?

---

### Post by fleamour on 2011-06-27
Under Synaptic "linux" has an exclamation mark next to it.  Installed version is:

2.6.35.28.36

Latest version:

2.6.35.30.38

---

### Post by fleamour on 2011-06-27
Could it be a server issue?

---

### Post by snowpine on 2011-06-27
I don't know the answer, I'm sorry. Maybe check the Synaptic documentation to see what the red exclamation mark signifies? (it doesn't sound like a good thing)

---

### Post by fleamour on 2011-06-27
Thanks for your help.  Two heads are better than one.  I removed some excess programs, historical crap, & it is no longer greyed out now.  

Maybe just coincidence, but panic aborted! 

:biggrin:\\:D/:biggrin:

---

### Post by IanW on 2011-06-27
For future reference, in Synaptic click "Help" then "Icon Legend".
A red exclamation mark means "Package Broken". This can often be repaired by typing "sudo apt-get -f install" in a terminal.

---

### Post by fleamour on 2011-06-27
Thanks, will try that next time.

Nice Dr. Who icon, not seen the latest & greatest but remember that one.

---

