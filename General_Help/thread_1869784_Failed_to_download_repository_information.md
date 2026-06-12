---
title: "Failed to download repository information"
date: 2011-10-26
forum: General Help
---

### Post by Angelus-Michael on 2011-10-26
Hi Everyone. I have a little problem with Ubuntu. When I'm selecting " Check For Updates" I'm receiving the following error " Failed to download repository information". In details appear "W:Failed to fetch copy:/var/lib/apt/lists/partial/ro.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead." 
Can somebody help me please?
Ps: i don't use Ubuntu for such a long time so please talk to me as you talk to a newbie Thanks a lot

---

### Post by IWantFroyo on 2011-10-26
Do you have a working Internet connection on that computer?

Try:
```
sudo apt-get update
```

If anything goes wrong, please post the output.

---

### Post by surfer on 2011-10-26
could you open a terminal and post the output of
```
$ cat /etc/apt/sources.list
```
and
```
$ cat /etc/apt/sources.list.d/*
```
and then run (and post the output of)
```
$ sudo apt-get update
```
that might help.

---

### Post by 3v3rgr33n on 2011-10-26
I think i might have had the same problem at first. go to your synaptic package manager->settings 
you should see something about reposities..try to choose the right one

---

### Post by Angelus-Michael on 2011-10-26
[COLOR=RoyalBlue][FONT=Comic Sans MS]***This is what i get:(***[/FONT][/COLOR]
```
michael@michael-eME728:~$  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
michael@michael-eME728:~$ cat /etc/apt/sources.list.d/*
deb http://archive.canonical.com/ubuntu oneiric partner #Added by software-center
michael@michael-eME728:~$ $ sudo apt-get update
$: command not found
michael@michael-eME728:~$  sudo apt-get update
[sudo] password for michael: 
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://security.ubuntu.com oneiric-security Release
Hit http://security.ubuntu.com oneiric-security/main Sources    
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Ign http://ro.archive.ubuntu.com oneiric InRelease             
Ign http://ro.archive.ubuntu.com oneiric-updates InRelease
Ign http://ro.archive.ubuntu.com oneiric-backports InRelease
Hit http://ro.archive.ubuntu.com oneiric Release.gpg
Hit http://ro.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://ro.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://ro.archive.ubuntu.com oneiric Release
Hit http://ro.archive.ubuntu.com oneiric-updates Release                       
Hit http://ro.archive.ubuntu.com oneiric-backports Release                     
Hit http://ro.archive.ubuntu.com oneiric/main Sources                          
Hit http://ro.archive.ubuntu.com oneiric/restricted Sources
Hit http://ro.archive.ubuntu.com oneiric/universe Sources
Hit http://ro.archive.ubuntu.com oneiric/multiverse Sources
Hit http://ro.archive.ubuntu.com oneiric/main i386 Packages
Hit http://ro.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://ro.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://ro.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://ro.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-updates/main Sources
Hit http://ro.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://ro.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://ro.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://ro.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-backports/main Sources
Hit http://ro.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://ro.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://ro.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://ro.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://ro.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://ro.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://ro.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://ro.archive.ubuntu.com oneiric/universe Translation-en
Hit http://ro.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://ro.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://ro.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://ro.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://ro.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://ro.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://ro.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://ro.archive.ubuntu.com oneiric-backports/universe Translation-en
Get:1 http://ro.archive.ubuntu.com oneiric/main Translation-en [3,719 kB]
Fetched 1 B in 6s (0 B/s)                    
W: Failed to fetch copy:/var/lib/apt/lists/partial/ro.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by surfer on 2011-10-26
strange...

what happens, if you (temporarily) remove all the "ro." parts of the url and connect directly to "archive.ubuntu.com" in the file /etc/apt/sources.list and then run
```
$ sudo apt-get update
```
again?

---

### Post by Angelus-Michael on 2011-10-26
> **surfer said:**
> strange...

what happens, if you (temporarily) remove all the "ro." parts of the url and connect directly to "archive.ubuntu.com" in the file /etc/apt/sources.list and then run
```
$ sudo apt-get update
```again?

And how should i remove all the "ro." parts?:(
I told you I'm newbie... I used to use Windows... I'm using Ubuntu since 1 October this year

---

### Post by surfer on 2011-10-26
oh, sorry! try this:
```
$ sudo gedit /etc/apt/sources.list
```

---

### Post by Angelus-Michael on 2011-10-26
This one is in terminal
```
(gedit:4326): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KH5Q3V': No such file or directory

(gedit:4326): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```
And this one appears in gedit
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ro.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

---

### Post by surfer on 2011-10-26
or (and this may be much simpler): open the Ubuntu Software Center, then Edit -> Software Sources.
in the middle of the window that appears, there should be something like "Download from: Server for Romania". Change that to "Download from: Main Server". then run ```
$ sudo apt-get update
``` again.

---

### Post by Angelus-Michael on 2011-10-26
Done. Thanks a lot. It works. God i hate this country!

---

