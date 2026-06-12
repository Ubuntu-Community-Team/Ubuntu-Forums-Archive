---
title: "Gimp Install Problem"
date: 2010-09-26
forum: General Help
---

### Post by Torombolo on 2010-09-26
I get an error while trying to install it viaw USC and via terminal....


```
[CODE]root@Toro:/home/carlos# apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies: 
  gimp: Depends: libgegl-0.0-0 (>= 0.1.3-2010072601~ll) but it is not going to be installed
E: Broken packages
root@Toro:/home/carlos# ^C
root@Toro:/home/carlos# apt-get install libgegl-0.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies: 
  libgegl-0.0-0: Depends: libumfpack5.4.0 (>= 1:3.4.0) but it is not installable
E: Broken packages
```[/CODE]

---

### Post by sanderd17 on 2010-09-26
What happens when you do a 

```

sudo apt-get update

```

Or if you try with aptitude instead of apt-get?

---

### Post by snowpine on 2010-09-26
I also would be curious to see the output of your "sudo apt-get update"; is it possible you have mixed up your software sources, or that your system is not up-to-date?

You can also try:

```
sudo apt-get -f install
```

---

### Post by Torombolo on 2010-09-26
```
carlos@Toro:~$ su
Password: 
root@Toro:/home/carlos# apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                      
Hit http://archive.ubuntu.com lucid Release.gpg                      
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://wine.budgetdedicated.com jaunty Release.gpg               
Ign http://wine.budgetdedicated.com/apt/ jaunty/main Translation-en_US
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Hit http://wine.budgetdedicated.com jaunty Release                             
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://archive.ubuntu.com lucid/multiverse Packages                        
Hit http://ppa.launchpad.net lucid/main Packages                               
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://archive.ubuntu.com lucid/universe Packages                          
Hit http://wine.budgetdedicated.com jaunty/main Packages             
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Reading package lists... Done
root@Toro:/home/carlos# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  diff
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Toro:/home/carlos# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
root@Toro:/home/carlos# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  diff
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Toro:/home/carlos# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
root@Toro:/home/carlos# apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  diff
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Toro:/home/carlos# 

```

---

### Post by snowpine on 2010-09-26
I would not recommend mixing Jaunty and Lucid repositories (software sources).

---

### Post by Torombolo on 2010-09-26
Removed the Jaunty source, Fixed the Flash nonfree Errors.

still when trying to install gimp is asking me for the libs.

---

### Post by snowpine on 2010-09-26
> **Torombolo said:**
> Removed the Jaunty source, Fixed the Flash nonfree Errors.

still when trying to install gimp is asking me for the libs.

It looks like you are trying to install a newer version of gimp from a 3rd party software source:

```
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ lucid/main Translation-en_US
```

I'd recommend contacting the maintainer of this PPA for help as it is not supported by the default Ubuntu install.

---

### Post by Torombolo on 2010-09-28
installed ubuntu again from 0, since i accidently deleted a partition and the grub would not boot anything, Re did my resources, and i found out i forgot a command to get the Libs in order to install gimp LOL... working now, il post what i did to install it when i get home since im at shcool atm.


Thanks Guys

---

