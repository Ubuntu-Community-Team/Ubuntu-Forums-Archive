---
title: "Ubuntu Torrent Downloader"
date: 2009-12-16
forum: General Help
---

### Post by D4Y.V on 2009-12-16
Fast Question, need to download some TOTALLY LEGAL MATERIAL in .torrent form, I checked Google, and I just got ways to Download the Ubuntu Software rather then a Downloader to use within the software.
Lil' help guys? ^.-
Ubuntu 9.10

---

### Post by ean5533 on 2009-12-16
> **D4Y.V said:**
> Fast Question, need to download some TOTALLY LEGAL MATERIAL in .torrent form, I checked Google, and I just got ways to Download the Ubuntu Software rather then a Downloader to use within the software.
Lil' help guys? ^.-
Ubuntu 9.10

The BitTorrent client Transmission comes installed with Ubuntu 9.10 by default, so you should be able to just open a .torrent file and let it fly.

If, for some reason, Transmission isn't installed on your system, you can install it with this terminal command:

```
sudo apt-get install transmission
```

---

### Post by SuperSonic4 on 2009-12-16
Deluge is also a good gtk torrent client - but use their PPA instead of the repo version for an up to date deluge if you do

---

### Post by scouser73 on 2009-12-16
Deluge, is a torrent client.  Go to **System > Administration > Synaptic Package Manager**

In the search box type **Deluge** & right click & select **Mark For Installation** then click **Apply** & **Apply** once more.

Deluge will now be installed, you will be able to find Deluge in the Internet sub-menu.

---

### Post by D4Y.V on 2009-12-16
Oh, sweet!!
Thanks... now, is there a way to play .ISO files and what is the correct way to set up an originally window's install for Ubuntu?
Does Virtual Clone Drive work with Ubuntu?
Is it the same as a normal install? How would I play it?
Speaking of which how do you play .exe files on Ubuntu?

I figure instead of making a new topic, I'll just add some stuff here if that's cool.

---

### Post by SuperSonic4 on 2009-12-16
The word play gives connotations of music/video and gaming. Perhaps install is what you mean?

ISOs are disc images - best method is to burn them to a blank CD/DVD and then load it up as though it were a CD. You *can* mount as though it were a CD but I'm not too sure on how to do it

I think the loop command does much the same as VCD

A Normal install?

Generally they won't work. Wine can work with some but often native linux versions exist - we can give suggestions if we know what you use

---

### Post by MaxIBoy on 2009-12-16
You can mount an ISO as if it were just a normal CD drive. First, make a folder where you want the files to show up (the ["mountpoint."]("http://en.wikipedia.org/wiki/Mount_%28computing%29#Mount_point")) Then, do this in a terminal:
```
sudo mount -t iso9660 -o loop /location/of/iso/file.iso /location/of/mount/point
```You can drag and drop your iso file and your mountpoint folder into the open terminal window and it will automatically add the full name and path of each file, so you don't need to type it yourself.

You will be asked for your password, it's normal if nothing shows up as you type it (to stop people seeing how long your password is.)



VLC can play ISOs back directly as if they were CDs or DVDs, you don't need to mount them. You can find VLC in "add/remove software," "synaptic package manager," Or you can just install it from the terminal this way:
```
sudo apt-get install vlc
```



Finally, you can double-click the ISO and browse the files on it.

---

### Post by ean5533 on 2009-12-16
> **D4Y.V said:**
> Thanks... now, is there a way to play .ISO files
ISO files can be mounted in Ubuntu without any special software needed. I'm not near an Ubuntu computer at the moment but I believe it's as simple as right-clicking the ISO file and picking "Mount Image" or something like that from the menu.



> **D4Y.V said:**
> what is the correct way to set up an originally window's install for Ubuntu?
I'm not sure I understand what your question is here. Are you asking how to import your settings from Windows?

> **D4Y.V said:**
> Does Virtual Clone Drive work with Ubuntu?
No, but again ISO files can be handled natively by Ubuntu, no software needed.

> **D4Y.V said:**
> Speaking of which how do you play .exe files on Ubuntu?
Now THAT's a more complicated question. .exe files are programs that are written for Windows, and the short answer is the .exe files are not supported directly by Linux.  However, there is a Linux program called WINE that can run .exe file with pretty good reliability. You can read more about WINE here:

[http://www.winehq.org/about/]("http://www.winehq.org/about/")

With the exception of video games, most Windows programs have some sort of equivalent on Linux, so usually .exe files aren't needed. (Usually.)

---

### Post by D4Y.V on 2009-12-16
OK, so, I'll explain in the most detail.
I am downloading Metal Gear Solid 1 for PC LEGALLY in torrents. [I bought the PC version years ago and have sinse lost it in the relics of time. I have the PS1 version though, which I adore]
I want to use the ISO to install the game into Ubuntu.
However the game is a PC game in that it is built for Windows Software.
The question about .EXE formats is that I want to run the OtaClock that I so desire. 

Is that enough? ^^'

---

### Post by MaxIBoy on 2009-12-16
You can see whether any program will work under WINE using this database:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=793](http://appdb.winehq.org/objectManager.php?sClass=application&iId=793)

[WINE](http://en.wikipedia.org/wiki/Wine_(software)) stands for **W**ine **I**s **N**ot an **E**mulator. It is a compatibilty layer for running some Windows software on Linux, OS X, BSD, and a few others.

As long as you have the CD key still, I don't think you're doing anything wrong...

---

### Post by D4Y.V on 2009-12-17
Is there a simple way to install Wine, I tried the Ubuntu Software Centre but I got "The action would require the installation of packages from not authenticated sources."
This is so complicated for me...-.-'

---

### Post by ean5533 on 2009-12-17
> **D4Y.V said:**
> Is there a simple way to install Wine, I tried the Ubuntu Software Centre but I got "The action would require the installation of packages from not authenticated sources."
This is so complicated for me...-.-'
You should be able to install the program by opening up a terminal and typing:

```
sudo apt-get install wine
```

It will ask you for permission (yes/no), so type "Y" and press enter. After that, WINE will be installed.

---

### Post by D4Y.V on 2009-12-17
I fear that something has gone wrong...
```
dave@dave-desktop:~$ sudo apt-get install wine
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
dave@dave-desktop:~$ 

```
Broken Packages DEFINITELY doesn't sound good.

---

### Post by ean5533 on 2009-12-17
> **D4Y.V said:**
> I fear that something has gone wrong...
```
dave@dave-desktop:~$ sudo apt-get install wine
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
dave@dave-desktop:~$ 

```
Broken Packages DEFINITELY doesn't sound good.

Can you please post the output of the following command?

```
sudo cat /etc/apt/sources.list
```

---

### Post by D4Y.V on 2009-12-17
Kindly,
```
dave@dave-desktop:~$ sudo cat /etc/apt/sources.list
[sudo] password for dave: 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by Darael on 2009-12-17
Right, and could you further post the output of ```
sudo sh -c "ls /etc/apt/sources.list.d; cat /etc/apt/sources.list.d/*"
```?
Thanks for helping us help you!

---

### Post by D4Y.V on 2009-12-17
I'd say no problem but then I'd be taking credit for mindlessly following orders like some sort of Soldier.
```
dave@dave-desktop:~$ sudo sh -c "ls /etc/apt/sources.list.d; cat /etc/apt/sources.list.d/*"
[sudo] password for dave: 
karmic-partner.list      ubuntu-wine-ppa-karmic.list
karmic-partner.list.save  ubuntu-wine-ppa-karmic.list.save
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu karmic partner
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu karmic partner
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main

```

---

### Post by Darael on 2009-12-17
Right, so it looks like your package manager hasn't realised the existence of the "wine1.2" package, which the "wine" package needs. Therefore, the cure **should** be as simple as removing any of wine (and system config) that's currently installed, then updating the repository information and trying again - all of which can be done thus:
```
sudo sh -c "aptitude purge wine; aptitude update; aptitude install wine"
```
If that doesn't work, then try replacing "wine" above with "wine1.2" - if **that** doesn't work, something is very wrong...

---

### Post by D4Y.V on 2009-12-17
```
dave@dave-desktop:~$ sudo sh -c "aptitude purge wine; aptitude update; aptitude install wine"
[sudo] password for dave: 
Sorry, try again.
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

Hit http://archive.canonical.com karmic Release.gpg                             
Ign http://archive.canonical.com karmic/partner Translation-en_GB               
Hit http://archive.canonical.com karmic Release                                 
Hit http://archive.canonical.com karmic/partner Packages                        
Hit http://archive.canonical.com karmic/partner Sources                         
Hit http://security.ubuntu.com karmic-security Release.gpg                      
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB           
Hit http://archive.ubuntu.com karmic Release.gpg                                
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]                        
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                      
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB       
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB     
Hit http://security.ubuntu.com karmic-security Release                          
Hit http://archive.ubuntu.com karmic Release                                    
Get:2 http://ppa.launchpad.net karmic Release [66.0kB]                          
Ign http://ppa.launchpad.net karmic Release                                     
Hit http://security.ubuntu.com karmic-security/main Packages                    
Hit http://archive.ubuntu.com karmic/main Sources                               
Hit http://ppa.launchpad.net karmic/main Packages                               
Hit http://security.ubuntu.com karmic-security/restricted Packages              
Hit http://security.ubuntu.com karmic-security/restricted Sources               
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://archive.ubuntu.com karmic/restricted Sources              
Hit http://gb.archive.ubuntu.com karmic Release.gpg                  
Get:3 http://gb.archive.ubuntu.com karmic/main Translation-en_GB [63.7kB]
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Get:4 http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB [3,402B] 
Get:5 http://gb.archive.ubuntu.com karmic/universe Translation-en_GB [33.2kB]   
Get:6 http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB [43.8kB] 
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB    
Hit http://gb.archive.ubuntu.com karmic Release                                 
Hit http://gb.archive.ubuntu.com karmic-updates Release                         
Hit http://gb.archive.ubuntu.com karmic/main Packages                           
Hit http://gb.archive.ubuntu.com karmic/restricted Packages                     
Hit http://gb.archive.ubuntu.com karmic/restricted Sources                      
Hit http://gb.archive.ubuntu.com karmic/main Sources                            
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources                      
Hit http://gb.archive.ubuntu.com karmic/universe Sources                        
Hit http://gb.archive.ubuntu.com karmic/universe Packages                       
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages                     
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages                   
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages             
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources              
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources                    
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources              
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources                
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages               
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages             
Fetched 144kB in 17s (8,251B/s)                                                 
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Duplicate sources.list entry http://archive.canonical.com karmic/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_karmic_partner_binary-i386_Packages)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

```So do I have it now...?
EDIT: I tried the software centre again and...
"This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time."

sudo sh -c "aptitude purge wine1.2; aptitude update; aptitude install wine1.2"
```
dave@dave-desktop:~$ 
dave@dave-desktop:~$ sudo sh -c "aptitude purge wine1.2; aptitude update; aptitude install wine1.2"
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

Hit http://gb.archive.ubuntu.com karmic Release.gpg                             
Hit http://gb.archive.ubuntu.com karmic/main Translation-en_GB                  
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]                        
Hit http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB            
Hit http://gb.archive.ubuntu.com karmic/universe Translation-en_GB              
Hit http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB    
Hit http://archive.canonical.com karmic Release.gpg                             
Ign http://archive.canonical.com karmic/partner Translation-en_GB               
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                      
Hit http://gb.archive.ubuntu.com karmic Release                                 
Hit http://security.ubuntu.com karmic-security Release.gpg                      
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB           
Hit http://gb.archive.ubuntu.com karmic-updates Release                         
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB       
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB     
Hit http://archive.canonical.com karmic Release                                 
Hit http://security.ubuntu.com karmic-security Release                          
Get:2 http://ppa.launchpad.net karmic Release [66.0kB]                          
Ign http://ppa.launchpad.net karmic Release                                     
Hit http://gb.archive.ubuntu.com karmic/main Packages                           
Hit http://gb.archive.ubuntu.com karmic/restricted Packages                     
Hit http://gb.archive.ubuntu.com karmic/restricted Sources                      
Hit http://gb.archive.ubuntu.com karmic/main Sources                            
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources                      
Hit http://security.ubuntu.com karmic-security/main Packages                    
Hit http://archive.canonical.com karmic/partner Packages                        
Hit http://ppa.launchpad.net karmic/main Packages                               
Hit http://gb.archive.ubuntu.com karmic/universe Sources                        
Hit http://gb.archive.ubuntu.com karmic/universe Packages                       
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages                     
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages                   
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages             
Hit http://security.ubuntu.com karmic-security/restricted Packages              
Hit http://security.ubuntu.com karmic-security/restricted Sources               
Hit http://security.ubuntu.com karmic-security/main Sources                     
Hit http://security.ubuntu.com karmic-security/multiverse Sources               
Hit http://archive.canonical.com karmic/partner Sources                         
Hit http://archive.ubuntu.com karmic Release.gpg                                
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources              
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources                    
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources              
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources                
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages               
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages             
Hit http://archive.ubuntu.com karmic Release                                    
Hit http://archive.ubuntu.com karmic/main Sources                               
Hit http://security.ubuntu.com karmic-security/universe Sources                 
Hit http://security.ubuntu.com karmic-security/universe Packages                
Hit http://security.ubuntu.com karmic-security/multiverse Packages              
Hit http://archive.ubuntu.com karmic/restricted Sources                         
Fetched 308B in 15s (19B/s)                                                     
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  libaudio2{a} libmpg123-0{a} libopenal1{a} ttf-symbol-replacement{a} 
  ttf-tahoma-replacement{a} winbind{a} wine1.2 wine1.2-gecko{a} 
0 packages upgraded, 8 newly installed, 0 to remove and 8 not upgraded.
Need to get 22.5MB of archives. After unpacking 101MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  wine1.2 ttf-tahoma-replacement ttf-symbol-replacement 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": y
Unrecognised input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com karmic/main libaudio2 1.9.2-1 [84.6kB]       
Get:2 http://ppa.launchpad.net karmic/main ttf-symbol-replacement 1.1.34-0ubuntu1 [53.1kB]
Get:3 http://gb.archive.ubuntu.com karmic/universe libmpg123-0 1.7.3-0ubuntu1 [379kB]
Get:4 http://ppa.launchpad.net karmic/main ttf-tahoma-replacement 1.1.34-0ubuntu1 [90.8kB]
Get:5 http://ppa.launchpad.net karmic/main wine1.2 1.1.34-0ubuntu1 [9,297kB]    
Get:6 http://gb.archive.ubuntu.com karmic/universe libopenal1 1:1.8.466-2 [94.1kB]
Get:7 http://gb.archive.ubuntu.com karmic/multiverse wine1.2-gecko 1.0.0-0ubuntu3 [8,123kB]
Get:8 http://gb.archive.ubuntu.com karmic-updates/main winbind 2:3.4.0-3ubuntu5.1 [4,378kB]                                                                  
Fetched 22.5MB in 16min 10s (23.2kB/s)                                                                                                                       
Selecting previously deselected package ttf-symbol-replacement.
(Reading database ... 143803 files and directories currently installed.)
Unpacking ttf-symbol-replacement (from .../ttf-symbol-replacement_1.1.34-0ubuntu1_all.deb) ...
Selecting previously deselected package ttf-tahoma-replacement.
Unpacking ttf-tahoma-replacement (from .../ttf-tahoma-replacement_1.1.34-0ubuntu1_all.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.2-1_i386.deb) ...
Selecting previously deselected package libmpg123-0.
Unpacking libmpg123-0 (from .../libmpg123-0_1.7.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.8.466-2_i386.deb) ...
Selecting previously deselected package wine1.2.
Unpacking wine1.2 (from .../wine1.2_1.1.34-0ubuntu1_i386.deb) ...
Selecting previously deselected package wine1.2-gecko.
Unpacking wine1.2-gecko (from .../wine1.2-gecko_1.0.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package winbind.
Unpacking winbind (from .../winbind_2%3a3.4.0-3ubuntu5.1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up ttf-symbol-replacement (1.1.34-0ubuntu1) ...
Setting up ttf-tahoma-replacement (1.1.34-0ubuntu1) ...
Setting up libaudio2 (1.9.2-1) ...

Setting up libmpg123-0 (1.7.3-0ubuntu1) ...

Setting up libopenal1 (1:1.8.466-2) ...

Setting up wine1.2 (1.1.34-0ubuntu1) ...
procps stop/waiting

Setting up wine1.2-gecko (1.0.0-0ubuntu3) ...
Setting up winbind (2:3.4.0-3ubuntu5.1) ...
 * Starting the Winbind daemon winbind                                                                                                                [ OK ] 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
```
OMG ITS HERE I LOVE YOU GUYS!!! OMG OMG!!!!

---

### Post by Darael on 2009-12-17
You should have wine now, but you may want to add wine through the Software Centre just to be sure. To avoid the problem in the future, you need to add the key for the Wine repository, which you can do with: ```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list; sudo add-apt-repository ppa:ubuntu-wine/ppa
```
Just by way of explanation: this pair of commands removes the repository, then adds it again with a tool that should also add the signing key used to verify the packages. You'll need to update your package list, but since you're not installing any new packages immediately that won't be necessary straight away.

---

### Post by D4Y.V on 2009-12-17
```
dave@dave-desktop:~$ sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list; sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for dave: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
OK. now that that's all over and done with...
When I play MGS1 all I can hear is sound, no kick **** visuals!

---

### Post by ean5533 on 2009-12-17
> **D4Y.V said:**
> ```
dave@dave-desktop:~$ sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list; sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for dave: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
OK. now that that's all over and done with...
When I play MGS1 all I can hear is sound, no kick **** visuals!

There aren't any recent reviews, but the WINE app database shows [that this game doesn't always play too well]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1047"). You might try checking users' comments on that page to see if they have any tips on how to get it to run better.

---

### Post by D4Y.V on 2009-12-17
NOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!
Nowell, I read that MGS2 works great...
I wonder where I put *that* disk...
THANK YOU I LOVE YOU!!! This community is much nicer then when I was trying to install Windows 7 Beta... I got accused of Piracy, and I was told to calm down, because some people were finding my posts displeasing... I think a system should beable to support a Keyboard and Mouse in the USB hub, mirite?
THANKS AGAIN!!!

---

### Post by TyrantWave on 2009-12-17
Ubuntu should recognise a USB keyboard / mouse with no problem.

You said you have the PS1 version of MGS - why not try a PS1 emulator to run it?
If you go to Ubuntu Software Centre (You are using 9.10 yes?) you can try PCSX, a ps1 emulator.

---

### Post by ean5533 on 2009-12-17
> **TyrantWave said:**
> Ubuntu should recognise a USB keyboard / mouse with no problem.

You said you have the PS1 version of MGS - why not try a PS1 emulator to run it?
If you go to Ubuntu Software Centre (You are using 9.10 yes?) you can try PCSX, a ps1 emulator.

Ah yes, I didn't even think about that. PCSX works fantastically on Linux and I've never had it not play a playstation game for me.

---

### Post by Darael on 2009-12-17
> **ean5533 said:**
> Ah yes, I didn't even think about that. PCSX works fantastically on Linux and I've never had it not play a playstation game for me.

I too can report wonderful successes with PCSX - The only problem being getting a legal BIOS file - especially if you have (as I do) one of the more obscure PAL models!

---

### Post by D4Y.V on 2009-12-17
Aha, here's where the deciding line comes in...
How about Duel Disk CD's, that's the one thing that pisses me right off, I want an emulator that supports disk swaps!!!

---

### Post by D4Y.V on 2009-12-17
OK, now that I've downloaded it unawares to the Duel Disk Playback possibility, is there an official way to get a PS3 gamepad working on Ubuntu?

---

### Post by ean5533 on 2009-12-17
> **D4Y.V said:**
> OK, now that I've downloaded it unawares to the Duel Disk Playback possibility, is there an official way to get a PS3 gamepad working on Ubuntu?
It definitely handles disc swaps. I ran Final Fantasy VII on that emulator a long time ago and it handled disc swapping at disc 2 and 3.

As far as the PS3 gamepad, I've never tried before, but [this guide]("http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu") claims that it's not too hard to do. Give it a shot.

---

### Post by D4Y.V on 2009-12-18
The instructions on that site are inconceivable! when I try the things after I download the package, it comes up with errors!

---

### Post by ean5533 on 2009-12-18
> **D4Y.V said:**
> The instructions on that site are inconceivable! when I try the things after I download the package, it comes up with errors!
EDIT: I just realized you meant the PS3 gamepad, not PCSX. Unfortunately I can't help you with that, I've never tried before. Don't even own a PS3 controller to try. You can try googling around for a better guide, but that's the only advice I have.

---

### Post by D4Y.V on 2009-12-18
Thank you anyway^^

---

