---
title: "Update of Lucid-Bleed problems"
date: 2011-08-31
forum: General Help
---

### Post by passonno on 2011-08-31
Hi there,

I am having problems with updating,  as the update manager keeps choking and offering a partial upgrade,  and it will not allow me to update any lucid-bleed packages.  

Is it supposed to work this way,  or did I mess it up somehow?  

I am more concerned with the fact there is a security update for xulrunner that I cannot install because of this error.```

# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

#deb http://ppa.launchpad.net/dtl131/ppa/ubuntu lucid main
#deb-src http://ppa.launchpad.net/dtl131/ppa/ubuntu lucid main
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://ppa.launchpad.net/docky-core/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu lucid main
#deb http://ppa.launchpad.net/doctormo/ppa/ubuntu lucid main
#deb-src http://ppa.launchpad.net/doctormo/ppa/ubuntu lucid main
deb http://repository.spotify.com stable non-free
#deb http://ppa.launchpad.net/ferramroberto/extra/ubuntu lucid main deb-src
#deb-src http://ppa.launchpad.net/ferramroberto/extra/ubuntu lucid main
deb http://ppa.launchpad.net/supercollider/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/supercollider/ppa/ubuntu lucid main
```

---

### Post by plucky on 2011-09-01
> Hi there,

I am having problems with updating, as the update manager keeps choking and offering a partial upgrade, and it will not allow me to update any lucid-bleed packages.

Is it supposed to work this way, or did I mess it up somehow?

I am more concerned with the fact there is a security update for xulrunner that I cannot install because of this error.

What is the error?

From a terminal post output of ```
sudo apt-get update && sudo apt-get upgrade
```

If that works without any errors then try ```
sudo apt-get dist-upgrade
``` but make sure it doesn't try to remove anything that would stop your system running.

Good luck

---

### Post by passonno on 2011-09-01
Here's that output:  ```
Get:1 http://dl.google.com stable Release.gpg [198B]
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://linux.dropbox.com lucid Release                                     
Get:2 http://dl.google.com stable Release [1,347B]                             
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Get:3 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/supercollider/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ferramroberto/minitube/ubuntu/ lucid/main Translation-en_US
Get:4 http://dl.google.com stable/main Packages [1,197B]                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:5 http://security.ubuntu.com lucid-security Release [44.7kB]               
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://repository.spotify.com stable Release.gpg                           
Ign http://repository.spotify.com/ stable/non-free Translation-en_US           
Hit http://archive.canonical.com lucid Release                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid Release                                 
Ign http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://repository.spotify.com stable Release                               
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ricotz/docky/ubuntu/ lucid/main Translation-en_US 
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/vala-team/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/zeitgeist-sharp/daily/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                             
Hit http://ppa.launchpad.net lucid Release                             
Hit http://ppa.launchpad.net lucid Release       
Hit http://ppa.launchpad.net lucid Release       
Ign http://repository.spotify.com stable/non-free Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Get:6 http://security.ubuntu.com lucid-security/main Packages [204kB]          
Ign http://repository.spotify.com stable/non-free Packages                     
Hit http://ppa.launchpad.net lucid/main Packages                            
Hit http://ppa.launchpad.net lucid/main Sources                              
Hit http://ppa.launchpad.net lucid/main Packages                             
Hit http://ppa.launchpad.net lucid/main Packages                             
Hit http://ppa.launchpad.net lucid/main Packages                             
Hit http://repository.spotify.com stable/non-free Packages                   
Hit http://ppa.launchpad.net lucid/main Packages       
Hit http://ppa.launchpad.net lucid/main Packages       
Hit http://ppa.launchpad.net lucid/main Packages       
Hit http://ppa.launchpad.net lucid/main Packages       
Hit http://ppa.launchpad.net lucid/main Packages       
Hit http://ppa.launchpad.net lucid/main Packages       
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:8 http://security.ubuntu.com lucid-security/main Sources [62.1kB]
Get:9 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:10 http://security.ubuntu.com lucid-security/universe Packages [82.7kB]
Get:11 http://security.ubuntu.com lucid-security/universe Sources [25.1kB]
Get:12 http://security.ubuntu.com lucid-security/multiverse Packages [4,557B]
Get:13 http://security.ubuntu.com lucid-security/multiverse Sources [1,754B]
Fetched 428kB in 2s (153kB/s)                          
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net/docky-core/ppa/ubuntu/ lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_docky-core_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gettext vlc vlc-data vlc-nox vlc-plugin-pulse
The following packages will be upgraded:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common
  xulrunner-1.9.2
5 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 12.5MB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ lucid-security/main apache2-mpm-prefork 2.2.14-5ubuntu8.6 [2,426B]
Get:2 http://security.ubuntu.com/ubuntu/ lucid-security/main apache2.2-common 2.2.14-5ubuntu8.6 [290kB]
Get:3 http://security.ubuntu.com/ubuntu/ lucid-security/main apache2.2-bin 2.2.14-5ubuntu8.6 [2,631kB]
Get:4 http://security.ubuntu.com/ubuntu/ lucid-security/main apache2-utils 2.2.14-5ubuntu8.6 [160kB]
Get:5 http://security.ubuntu.com/ubuntu/ lucid-security/main xulrunner-1.9.2 1.9.2.21+build1+nobinonly-0ubuntu0.10.04.1 [9,430kB]
Fetched 12.5MB in 43s (289kB/s)                                                
(Reading database ... 167416 files and directories currently installed.)
Preparing to replace apache2-mpm-prefork 2.2.14-5ubuntu8.4 (using .../apache2-mpm-prefork_2.2.14-5ubuntu8.6_i386.deb) ...
 * Stopping web server apache2                                                   ... waiting .                                                           [ OK ]
Unpacking replacement apache2-mpm-prefork ...
Preparing to replace apache2.2-common 2.2.14-5ubuntu8.4 (using .../apache2.2-common_2.2.14-5ubuntu8.6_i386.deb) ...
Unpacking replacement apache2.2-common ...
Preparing to replace apache2.2-bin 2.2.14-5ubuntu8.4 (using .../apache2.2-bin_2.2.14-5ubuntu8.6_i386.deb) ...
Unpacking replacement apache2.2-bin ...
Preparing to replace apache2-utils 2.2.14-5ubuntu8.4 (using .../apache2-utils_2.2.14-5ubuntu8.6_i386.deb) ...
Unpacking replacement apache2-utils ...
Preparing to replace xulrunner-1.9.2 1.9.2.20+build1+nobinonly-0ubuntu0.10.04.1 (using .../xulrunner-1.9.2_1.9.2.21+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Removing obsolete conffile /etc/gre.d/1.9.2.20.system.conf ...
Unpacking replacement xulrunner-1.9.2 ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up apache2.2-bin (2.2.14-5ubuntu8.6) ...
Setting up apache2-utils (2.2.14-5ubuntu8.6) ...
Setting up apache2.2-common (2.2.14-5ubuntu8.6) ...

Setting up apache2-mpm-prefork (2.2.14-5ubuntu8.6) ...
 * Starting web server apache2                                           [ OK ] 

Setting up xulrunner-1.9.2 (1.9.2.21+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: using /usr/bin/xulrunner-1.9.2 to provide /usr/bin/xulrunner (xulrunner) in auto mode.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```  

What I am trying to avoid is a dist-upgrade,  unless you can tell me a reason why it's a good idea and maybe clear up a misconception,  namely,  that it would push me into 10.10,  when I am perfectly happy with LTS releases.

Thanks for your help,

Anthony

---

### Post by plucky on 2011-09-02
> W: Duplicate sources.list entry [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_docky-core_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

You have a duplicate entry for this ppa.Either use Software Sources to disable one of them or edit your sources.list and put a # in front of the line ```
deb http://ppa.launchpad.net/docky-core/ppa/ubuntu lucid main
```

> What I am trying to avoid is a dist-upgrade, unless you can tell me a reason why it's a good idea and maybe clear up a misconception, namely, that it would push me into 10.10, when I am perfectly happy with LTS releases.

The dist-upgrade command will **not** upgrade your system to 10.10,it sometimes fixes the request for a partial upgrade,but you have to make sure it doesn't try to remove something that is vital for your system to run.If you run it,read what it says before you tell it to go ahead.

The reason it is asking for a partial upgrade is because of > The following packages have been kept back:
  gettext vlc vlc-data vlc-nox vlc-plugin-pulse

Did you try to install vlc?

Try the dist-upgrade command and see if it has to remove something before it can install those packages.


Good Luck

---

### Post by passonno on 2011-09-02
Well,  

So there was not a visible duplicate in my sources.list,  but there were dupes in sources.list.d directory and sources.list.save.  

It probably has something to do with my mucking about trying to install Docky Stacks.  

I removed those dupes,  removed Docky,  reinstalled it,  and apt-get update works fine.  

As for the upgrade,  I actually do not remember where I got vlc from,  but it is trying to install vlc with Pulse plugins,  which I have explicity removed from my system,  for reasons of musical of production.

---

### Post by passonno on 2011-09-02
Everything is good now.  I removed vlc and installed it again,  and now update manager works perfectly.

---

### Post by uRock on 2011-09-02
dist-upgrade will not upgrade to the next release. It will install the updated kernel, if there is one. What version of Firefox do you have?

The xulrunner update will not install on my 10.04 machines either, but this is because I have Firefox 6.0.1 installed.

---

### Post by passonno on 2011-09-02
> **uRock said:**
> dist-upgrade will not upgrade to the next release. It will install the updated kernel, if there is one. What version of Firefox do you have?

The xulrunner update will not install on my 10.04 machines either, but this is because I have Firefox 6.0.1 installed.

I don't actually see any upgrades for it anymore,  which is fine for me because, since I removed Firefox at install,  I wouldn't see the need for that package.

---

