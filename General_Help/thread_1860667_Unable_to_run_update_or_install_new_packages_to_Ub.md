---
title: "Unable to run update or install new packages to Ubuntu 10.04"
date: 2011-10-15
forum: General Help
---

### Post by jasefest on 2011-10-15
Hi there,

I've been using Ubuntu for a few months (upgraded from Jaunty-Lucid) now and I love it! Big thanks goes to all the community for providing easy to follow instructions and terminal commands for me to C+P. This problem seems quite specific though. Any help would be greatly greatly appreciated.

When I try to install ANY package from the ubuntu software centre I get the following error:

> Requires installation of untrusted packages
The action would require the installation of packages from unauthenticated sources.

OK.. so what is the problem here?? I tried running an update using sudo apt-get update.. This is what I got.

> Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB       
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free Translation-en_GB           
Ign [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) lucid/main Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB             
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Packages                     
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB       
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Packages                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB         
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Packages                     
  407  Unauthorized
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB       
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
  407  Unauthorized
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  407  Unauthorized
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg            
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Err [http://dl.google.com](http://dl.google.com) stable/main Packages  
  407  Unauthorized
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
  407  Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
  407  Unauthorized
W: Failed to fetch [http://repository.spotify.com/dists/stable/non-free/binary-i386/Packages.gz](http://repository.spotify.com/dists/stable/non-free/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  407  Unauthorized

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  407  Unauthorized

E: Some index files failed to download, they have been ignored, or old ones used instead.


I have an inkling this is because i stupidly tried to edit the sources.list file while trying to install an Beta of Spotify (the music listening service) for linux. My first time trying this and I think I've f****d up somewhere along the way (didn't backup so don't ask).

The following is my etc/apt/sources.list file

> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Skype disabled on upgrade to karmic
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
# deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free

What can I do!?:confused:

---

### Post by Blaqksheep on 2011-10-15
Hi, may I get a bit more info?  Run a few terminal commands for me and paste the results from each one.

```
lsb_release -a

arch

ifconfig
```

Finally, try upgrading packages you have if possible.

```
sudo apt-get upgrade
```

---

### Post by jasefest on 2011-10-15
Hi, below are the results of the terminal commands you asked me to run.

> mike@mike-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
mike@mike-laptop:~$ arch
i686
mike@mike-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:09:d8:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.133.1  Bcast:192.168.133.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.210.1  Bcast:172.16.210.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:37:ca:d9  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe37:cad9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1499462 (1.4 MB)  TX bytes:660092 (660.0 KB)


---

### Post by jasefest on 2011-10-15
Can anyone please help or give me a hint as to what is wrong? I don't have to have to make a fresh install of Ubuntu do I?
:(

---

### Post by LKjell on 2011-10-15
Have you tried another mirror?

---

### Post by jasefest on 2011-10-15
Yes I have tried changing mirrors. The problem seems to be that Ubuntu thinks that my downloading of packages is "unauthorized". It says this for all the packages when I try to update. 

> 407 Unauthorized
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources



Am I missing the keys or something? How do I find out?

---

### Post by LKjell on 2011-10-16
Download this package and install it. 
[http://packages.ubuntu.com/lucid/ubuntu-keyring](http://packages.ubuntu.com/lucid/ubuntu-keyring)

---

### Post by jasefest on 2011-10-17
I reinstalled the ubuntu-keyring package, it appears thats not the problem. The situation is that currently I can't run any updates or install new packages. Can anyone point me in the direction of what the problem might be please as I'm quite lost..

---

