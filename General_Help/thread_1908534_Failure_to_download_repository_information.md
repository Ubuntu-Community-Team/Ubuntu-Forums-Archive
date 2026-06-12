---
title: "Failure to download repository information"
date: 2012-01-13
forum: General Help
---

### Post by That_1_guy on 2012-01-13
I'm trying to update my computer, i'm currently running ubuntu 11.10, and i keep getting this error when i try and update. i've already searched on here, and nothing has worked, and i'm getting pretty frustrated.:x

W:GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  InRelease: File /var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_InRelease doesn't start with a clearsigned message, W:Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_en  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.

any help would be fantastic, and if you could, make it easy for me to understand, i'm a relatively new user.

---

### Post by spacecheck on 2012-01-13
Perhaps you could try running the solution cited in this [post]("http://ubuntuforums.org/showthread.php?p=9406436#post9406436"):

[http://ubuntuforums.org/showthread.php?p=9406436#post9406436](http://ubuntuforums.org/showthread.php?p=9406436#post9406436)

It requires you to open the terminal (Ctrl+Alt+T) and then run the listed commands as super user, so you have to put sudo in front of them and enter your password.

If it works, please use the thread tools to mark this thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

If it doesn't work, report back for further input.

Good luck!

---

### Post by That_1_guy on 2012-01-13
i tried it, again, and i still didn't get anywhere with it. when i entered it into Terminal, i got these back:


keri@Decaulion:~$ sudo su apt-get clean
[sudo] password for keri: 
Unknown id: apt-get
keri@Decaulion:~$ sudo apt-get clean
keri@Decaulion:~$ sudo cd /var/lib/apt
sudo: cd: command not found
keri@Decaulion:~$ sudo mv lists list.old
mv: cannot stat `lists': No such file or directory
keri@Decaulion:~$ sudo mkdr -p lists/partial
sudo: mkdr: command not found
keri@Decaulion:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
keri@Decaulion:~$ sudo apt-get clean
kerid4209: command not found
keri@Decaulion:~$ sudo apt-get clean
keri@Decaulion:~$ sudo cd /var/lib/apt
sudo: cd: command not found
keri@Decaulion:~$ sudo cd/var/lib/apt
sudo: cd/var/lib/apt: command not found
keri@Decaulion:~$ 

if there's anything else i could try, it would be fantastic

---

### Post by spacecheck on 2012-01-13
First make sure all package managers, Software Sources, Update Managers are closed.
Then run the first line with sudo, 
then the second line without.
Then the rest of the lines with sudo.
After that, try ```
sudo apt-get upgrade
```It may then show a list of packages to upgrade and an option to select y/n.
Let me know how that works for you.

Remember, if it works, please use the thread tools to mark this thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Good luck!

---

### Post by That_1_guy on 2012-01-13
i tried it like you said, but to no avail. this is what was in the terminal window:


keri@Decaulion:~$ sudo apt-get clean
[sudo] password for keri: 

keri@Decaulion:~$ cd /var/lib/apt

keri@Decaulion:/var/lib/apt$ sudo mv lists lists.old

keri@Decaulion:/var/lib/apt$ sudo mkdir -p lists/partial

keri@Decaulion:/var/lib/apt$ sudo apt-get clean

keri@Decaulion:/var/lib/apt$ sudo apt-get update

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,228 B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:4 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security InRelease                    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Get:9 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5,922 B]                   
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,740 B]                      
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]      
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release.gpg [198 B]       
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release [40.8 kB]                  
Get:15 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources [2,255 B]          
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [510 B]                   
Get:17 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [524 B]                   
Get:18 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [3,943 B]    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [676 B]             
Get:20 [http://www.bashterritory.com](http://www.bashterritory.com)  InRelease [1,019 B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://www.bashterritory.com](http://www.bashterritory.com)  InRelease                                    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]          
Get:22 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [593 B]             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release [40.8 kB]        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release [40.8 kB]         
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Get:26 [http://www.bashterritory.com](http://www.bashterritory.com)  Packages [1,019 B]                        
28% [26 Packages bzip2 0 B] [25 Sources 107 kB/877 kB 12%] [Waiting for headersbzip2: (stdin) is not a bzip2 file.
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources [5,351 B]       
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]     
Get:29 [http://www.bashterritory.com](http://www.bashterritory.com)  Translation-en_US [1,019 B]             
Get:30 [http://www.bashterritory.com](http://www.bashterritory.com)  Translation-en [1,019 B]                  
31% [29 Translation-en_US bzip2 0 B] [28 Sources 754 kB/4,677 kB 16%] [Connectibzip2: (stdin) is not a bzip2 file.
31% [30 Translation-en bzip2 0 B] [28 Sources 754 kB/4,677 kB 16%] [Connecting bzip2: (stdin) is not a bzip2 file.
35% [26 Packages xz 0 B] [28 Sources 949 kB/4,677 kB 20%] [Connecting to [www.ba/usr/bin/xz:](www.ba/usr/bin/xz:) (stdin): File format not recognized
61% [29 Translation-en_US xz 0 B] [28 Sources 2,449 kB/4,677 kB 52%] [Connectin/usr/bin/xz: (stdin): File format not recognized
67% [30 Translation-en xz 0 B] [28 Sources 2,807 kB/4,677 kB 60%] [Connecting t/usr/bin/xz: (stdin): File format not recognized
87% [26 Packages lzma 0 B] [28 Sources 3,946 kB/4,677 kB 84%] [Connecting to ww/usr/bin/lzma: Decoder error
94% [29 Translation-en_US lzma 0 B] [28 Sources 4,337 kB/4,677 kB 92%] [Connect/usr/bin/lzma: Decoder error
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]        
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]      
95% [30 Translation-en lzma 0 B] [28 Sources bzip2 0 B] [32 Packages 879 kB/1,2/usr/bin/lzma: Decoder error
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B] 
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]  
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]  
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]    
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [111 kB]      
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [35.4 kB] 
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [2,916 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [253 kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [83.4 kB]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [4,976 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources [1,577 B]   
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources [5,882 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages [1,912 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages [6,405 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex [72 B]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [72 B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main Sources [23.1 kB]    
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted Sources [14 B] 
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Sources [8,189 B]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse Sources [653 B]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main i386 Packages [65.2 kB]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe i386 Packages [22.2 kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse i386 Packages [1,653 B]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [71 B]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en [701 kB]       
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB] 
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [118 kB]
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [3,000 B]
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en [508 B]
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en [50.8 kB]
Get:84 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en [1,203 B]
Get:85 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en [14 B]
Get:86 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en [14 B]
Get:87 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en [5,524 B]
Get:88 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/main Translation-en [34.5 kB]
Get:89 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/multiverse Translation-en [840 B]
Get:90 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/restricted Translation-en [14 B]
Get:91 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security/universe Translation-en [16.0 kB]
Fetched 16.6 MB in 21s (775 kB/s)                                              
W: GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  InRelease: File /var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_en%5fUS  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

i'm willing to try anything short of re-installing, but this is annoying me to no end.

---

### Post by spacecheck on 2012-01-13
Patience is a virtue.

You need to keep all the package managers closed and then open the file /etc/apt/source.list and copy the contents in a response, so I can see what needs to be changed and let you know.

Chin up !

---

### Post by That_1_guy on 2012-01-13
whats with the decoder errors?

and here's the source list you asked for:

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /

---

### Post by spacecheck on 2012-01-13
With the package managers still closed, you need to 
```
sudo gedit /etc/apt/sources.list
``` and put a hash mark # in front of:
```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
``` and in front of:```
deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /     
```Then save the file and rerun the previously mentioned commands in the manner cited in my earlier post.

Let me know how it works then.

Good luck!

---

### Post by That_1_guy on 2012-01-13
is it one hash mark, or two?

---

### Post by spacecheck on 2012-01-13
> **That_1_guy said:**
> is it one hash mark, or two?
One hash mark # means it should be ignored by the system, two means it will probably also be ignored by the user...

One # is enough to stop the system from accessing that package source. Two hash marks ## are enough to make the user ignore the instructions/explanation intended to help the user understand what is done.

:-)

Remember, if it works, please use the thread tools to mark this thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Good luck!

---

### Post by That_1_guy on 2012-01-13
whenever i try to move lists, i get this error:


keri@Decaulion:/var/lib/apt$ sudo mv lists lists.old
mv: cannot move `lists' to `lists.old/lists': Directory not empty

what does that mean? and how can i fix it?

This also shows up when i go to edit the sources list:


keri@Decaulion:~$ sudo gedit /etc/apt/sources.list
[sudo] password for keri: 

(gedit:2213): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NCG47V': No such file or directory

(gedit:2213): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by spacecheck on 2012-01-13
> **That_1_guy said:**
> whenever i try to move lists, i get this error:


keri@Decaulion:/var/lib/apt$ sudo mv lists lists.old
mv: cannot move `lists' to `lists.old/lists': Directory not empty

what does that mean? and how can i fix it?

Let's see if we can do without, since we are changing the sources.list otherwise we may need to remove it.

> This also shows up when i go to edit the sources list:


keri@Decaulion:~$ sudo gedit /etc/apt/sources.list
[sudo] password for keri: 

(gedit:2213): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NCG47V': No such file or directory

(gedit:2213): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directoryThis just means it will not be possible for the editor to add an entry to the "recent documents" list, since this does not exist for the super user account. It can be ignored for the moment. Just put the hash marks in the cited spots like the other lines with a single hash mark and save the file.
Then just run ```
sudo apt-get update
sudo apt-get upgrade
``` and see what we get.

Good luck!

---

### Post by That_1_guy on 2012-01-13
it worked this time! thanks for all the help, and dealing with my lack of patience, lol

---

### Post by spacecheck on 2012-01-13
> **That_1_guy said:**
> it worked this time! thanks for all the help, and dealing with my lack of patience, lol
Great! My pleasure! Glad it worked!

Have fun!

---

### Post by amittan on 2012-08-29
> **spacecheck said:**
> Patience is a virtue.

You need to keep all the package managers closed and then open the file /etc/apt/source.list and copy the contents in a response, so I can see what needs to be changed and let you know.

Chin up !
Dear,
I am struggling with apt-get update problem. 
Sending source list file details as: # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Also errors as:
sudo apt-get update
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease [2,601 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease 
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [2,601 B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
100% [2 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]          
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [2,601 B]            
100% [5 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Connecbzip2: (stdin) is not a bzip2 file.
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex [2,601 B]         
Get:7 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4,005 B]           
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,033 B]     
90% [2 Sources xz 0 B] [Waiting for headers] [Waiting for headers] [Waiting for/usr/bin/xz: (stdin): File format not recognized
90% [5 Packages xz 0 B] [Waiting for headers] [Waiting for headers] [Connecting/usr/bin/xz: (stdin): File format not recognized
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
90% [2 Sources lzma 0 B] [Waiting for headers] [Waiting for headers] [Waiting f/usr/bin/lzma: (stdin): File format not recognized
90% [5 Packages lzma 0 B] [Waiting for headers] [Waiting for headers] [Connecti/usr/bin/lzma: (stdin): File format not recognized
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]                 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [5,019 kB]           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources [155 kB]           
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]         
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]     
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex [3,706 B]       
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B] 
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B] 
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [158 kB]         
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]  
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [50.1 kB]    
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]  
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [378 kB]   
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [127 kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources [2,422 B]      
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources [14 B]   
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources [13.5 kB]  
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [12.0 kB]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex [71 B]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en [726 kB]          
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]   
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en [2,395 B]   
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en [3,341 kB]    
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [182 kB]  
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en [5,414 B]
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en [1,484 B]
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [75.6 kB]
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en [1,244 B]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en [422 B]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en [8,807 B]
Fetched 17.7 MB in 27s (633 kB/s)                                              
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

Please help me to get out of this problem!!!

---

