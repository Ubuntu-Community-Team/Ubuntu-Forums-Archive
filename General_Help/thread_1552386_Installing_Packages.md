---
title: "Installing Packages"
date: 2010-08-13
forum: General Help
---

### Post by Noorani on 2010-08-13
Hello,
I just started having a problem with my ubuntu Jaunty.
When I try installing Gimp and VLC through Synaptic I get the following error
**Could not mark all packages for installation or upgrade**
The following packages have unresolvable dependancies. Make sure that all repositories are added and enabled in the preferences

gimp:
  Depends: libgimp2.0 (>=2.6.10) but 2.6.6-0ubuntu1.1 is to be installed
  Depends: libatk1.0-0 (>=1.29.3) but 1.26.0-0ubuntu2 is to be installed
  Depends: libc6 (>=2.11) but 2.9-4ubuntu6.2 is to be installed
I get similar message for VLC as well
I installed Amarok after this problem started and it installed properly.
Could anyone please help

---

### Post by snowpine on 2010-08-13
Is your system up-to-date? I think you can do this from within Synaptic, or else use the Update Manager. The newer version of Gimp and VLC may depend on packages that are out-of-date, an upgrade should fix this.

---

### Post by Noorani on 2010-08-13
Actually I am unable to upgrade my computer.When I use Update Manager, as soon as I open it I get an error message as follows:

**Could not calculate the upgrade**
An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

And when I click on Install updates I get the error message:

Could not apply changes!
Fix broken packages first.
Thanks

---

### Post by davidmohammed on 2010-08-13
open a terminal session and run the following


sudo apt-get clean 
sudo apt-get auto clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by snowpine on 2010-08-13
Hmmm, you haven't messed with your software sources, have you? What is the output of:

```
cat /etc/apt/sources.list
sudo apt-get -f install
```

---

### Post by Noorani on 2010-08-13
Terminal:

mknoorani@mknoorani-desktop:~$ sudo apt-get clean
[sudo] password for mknoorani: 
mknoorani@mknoorani-desktop:~$ sudo apt-get auto clean
E: Invalid operation auto
mknoorani@mknoorani-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mknoorani@mknoorani-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Translation-en_US
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/universe Translation-en_US
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates Release.gpg                 
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/main Translation-en_US      
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/universe Translation-en_US  
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty Release                                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Sources                        
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates Release                     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/main Packages                
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/main Sources                
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/restricted Sources          
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/universe Packages           
Hit [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/universe Sources            
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                    
Fetched 308B in 5s (55B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5DC4E17435661D98
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
mknoorani@mknoorani-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  kompozer libgimp2.0 transmission-common transmission-gtk vlc-nox
The following packages will be upgraded:
  adobe-flashplugin tzdata
2 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 5563kB of archives.
After this operation, 152kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner adobe-flashplugin 10.1.82.76-1jaunty1 [4881kB]
Get:2 [http://ke.archive.ubuntu.com](http://ke.archive.ubuntu.com) jaunty-updates/main tzdata 2010k~repack-0ubuntu0.9.04 [682kB]
Fetched 5563kB in 3min 3s (30.4kB/s)                                           
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages)
Preconfiguring packages ...
(Reading database ... 163820 files and directories currently installed.)
Preparing to replace tzdata 2010j~repack-0ubuntu0.9.04 (using .../tzdata_2010k~repack-0ubuntu0.9.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2010k~repack-0ubuntu0.9.04) ...

Current default timezone: 'Africa/Nairobi'
Local time is now:      Fri Aug 13 22:46:46 EAT 2010.
Universal Time is now:  Fri Aug 13 19:46:46 UTC 2010.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 163826 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.1.53.64-1jaunty1 (using .../adobe-flashplugin_10.1.82.76-1jaunty1_i386.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (10.1.82.76-1jaunty1) ...

mknoorani@mknoorani-desktop:~$ 



I am still unable to install the software mentioned earlier

---

### Post by Noorani on 2010-08-13
Terminal:

mknoorani@mknoorani-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty-updates universe

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
# deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiversedeb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb [http://ppa.launchpad.net/suraia/ppa/ubuntu](http://ppa.launchpad.net/suraia/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) jaunty main

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
mknoorani@mknoorani-desktop:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mknoorani@mknoorani-desktop:~$

---

### Post by snowpine on 2010-08-13
Your software sources are a troubling mix of Intrepid, Jaunty, Lucid, plus many unsupported 3rd-party repositories. :(

I would suggest scaling back to the official repositories until you have restored your system to a working state (if such is even possible).

To do so, edit your sources.list file:

```
gksu gedit /etc/apt/sources.list
```

Type a # symbol at the start of any questionable line in the file. This will comment it out so it's skipped. (You can always delete the # at a later date to add the repo back in.)

If you need to generate a new sources.list: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

(edit) ps don't forget to check /etc/apt/sources.list.d/ for additional software source files.

---

### Post by Noorani on 2010-08-13
snowpipe, I don't understand what you mean my questionable line. Please explain as I am still a bit of a new user
Thanks for your response

---

### Post by davidmohammed on 2010-08-13
in the sources.list file search for intrepid.  For any line that contains intrepid, add a # at the beginning of the line.

repeat this but with the search term lucid.

save the file

then repeat the commands in my post above.

---

### Post by snowpine on 2010-08-13
> **Noorani said:**
> snowpipe, I don't understand what you mean my questionable line. Please explain as I am still a bit of a new user
Thanks for your response

You added these questionable software sources yourself. They are not part of a normal Ubuntu install. Doing so has created an impossible situation, and Ubuntu can't update or install packages until you resolve the conflict.

I have no experience running a mixed intrepid/jaunty/lucid system, so I don't want to give you any unqualified advice that will potentially make the situation worse. If you want to see what your software sources "should" look like, use the link in post #8.

---

### Post by Noorani on 2010-08-13
I dont understand all this software sources stuff.Is it that we can't add software sources by ourselves or what? because when I was a completely new user I used to just follow instructions given to me for installing software(I'm not sure I followed those instructions perfectly correctly). I think I will have to do some research and reading on the subject. Since I was thinking of installing Lucid on my computer in October I think I can make it two months earlier and install it now
Anyway thanks for all the help guys.
Cheers!

---

### Post by snowpine on 2010-08-13
> **Noorani said:**
> I dont understand all this software sources stuff.Is it that we can't add software sources by ourselves or what? because when I was a completely new user I used to just follow instructions given to me for installing software(I'm not sure I followed those instructions perfectly correctly). I think I will have to do some research and reading on the subject. Since I was thinking of installing Lucid on my computer in October I think I can make it two months earlier and install it now
Anyway thanks for all the help guys.
Cheers!

No worries; I know it is confusing... let me try to explain.

Ubuntu is not like Windows. Imagine you want to eat a sandwich. Microsoft just gives you the bread (Windows). If you want meat, cheese, lettuce, mustard, etc. (the different software apps like browser, office, photoshop, games, etc.) you have to buy each one separately, take them home, make the sandwich yourself. If the sandwich tastes bad or makes you sick, Microsoft says "not our fault!"

Ubuntu is like going to the deli and buying a whole sandwich. All of the ingredients (the core OS, browser, office suite, games, movie player, etc.) come from the same place (the Ubuntu repository) and are designed to taste good together. So long as you get everything from this one trusted source, you won't get a tummy ache. Every 6 months, you get a new sandwich (Ubuntu release) and everything tastes great. They support the whole sandwich, not just the bread.

Are you with me so far? Now let me explain how a lot of Ubuntu users get into trouble. They say "this Ubuntu sandwich tastes really good, but there is a new kind of cheese I want, or maybe I want a different pickle, and how about a tomato from this store." Or, maybe the sandwich starts to taste stale, so you go out and get some fresher ingredients. This is what happens when you add software sources.

If you are careful, you can add a few trusted software sources and you'll probably be okay. But if you mix together a bunch of software sources for different Ubuntu releases (Intrepid/Jaunty/Karmic/Lucid) you get a big mess. Your sandwich gets too big, and when you try to take a bite, everything squishes out the other end.

So whether you stick with Jaunty and try to fix it, or you do a fresh install of Lucid, next time your sandwich will taste better because you understand how it works. :)

---

### Post by Noorani on 2010-08-14
Good explanation. sorry for delay in response, I had gone to sleep.
Anyway, I understand what you mean but how do you know whether the software source that you want to add is a trusted software source (i.e. not for a different release). Is there any way of finding out so I can avoid such a problem in future.
Thanks

---

### Post by snowpine on 2010-08-14
> **Noorani said:**
> Good explanation. sorry for delay in response, I had gone to sleep.
Anyway, I understand what you mean but how do you know whether the software source that you want to add is a trusted software source (i.e. not for a different release). Is there any way of finding out so I can avoid such a problem in future.
Thanks

You can ask around on these forums if you're wondering whether a software source is safe to use. :)

Also you need to know which Ubuntu release you are using (jaunty/karmic/lucid/etc) and only use software sources that match!

In general, if the application you're looking for is available from the standard Ubuntu repositories, that is the safest place to get it.

---

### Post by Noorani on 2010-08-14
Thanks for all the help folks. Really appreciate it!

---

