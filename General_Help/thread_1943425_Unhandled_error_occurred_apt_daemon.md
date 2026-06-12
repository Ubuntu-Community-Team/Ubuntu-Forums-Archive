---
title: "Unhandled error occurred apt daemon"
date: 2012-03-19
forum: General Help
---

### Post by Hookheathen on 2012-03-19
I have recently upgraded to 11.10 and was installing some extra programs and got this warning message. Could anyone help please? Do I have to start afresh with a complete reinstall?
Thanks.

---

### Post by raja.genupula on 2012-03-19
please post the output of 
```
sudo apt-get update 
sudo apt-get upgrade 
```

and please place between icode tags by clicking at # in this window .

---

### Post by Hookheathen on 2012-03-19
Hi Raja,

I am sorry if this is long but here are the outputs of the two codes:-

#michael@michael-ThinkPad-X31:~$ sudo apt-get update 
```
[sudo] password for michael: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security InRelease                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg                           
Get:1 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security Release.gpg [198 B]        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Get:7 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5,922 B]                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                               
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release [40.8 kB]           
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease                                 
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security Release [40.8 kB]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release                     
Get:11 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [3,941 B]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [1,851 B]                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en             
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [2,706 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en             
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [34.5 kB]      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [12.9 kB]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,654 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [90.4 kB]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources [130 kB]      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [31.0 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,362 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [21.8 kB]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages                        
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources [47.5 kB]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex                     
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,648 B]
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages [300 kB]
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages [103 kB]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,359 B]
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main Sources [34.5 kB]
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted Sources [14 B] 
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe Sources [12.9 kB]
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse Sources [1,654 B]
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main i386 Packages [90.4 kB]
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe i386 Packages [31.0 kB]
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse i386 Packages [3,362 B]
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en [62.1 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main Translation-en          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted Translation-en
Get:52 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe Translation-en [21.8 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en_GB
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en
Fetched 1,196 kB in 3s (309 kB/s)
Reading package lists... Done
michael@michael-ThinkPad-X31:~$ 
#
Replacing files in old package language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:11.10+20120103 (using .../language-pack-gnome-en_1%3a11.10+20120306_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Replacing files in old package language-pack-gnome-en-base ...
Preparing to replace app-install-data-partner 12.11.10.1 (using .../app-install-data-partner_12.11.10.2_all.deb) ...
Unpacking replacement app-install-data-partner ...
Preparing to replace firefox-globalmenu 10.0.2+build1-0ubuntu0.11.10.1 (using .../firefox-globalmenu_11.0+build1-0ubuntu0.11.10.1_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 10.0.2+build1-0ubuntu0.11.10.1 (using .../firefox_11.0+build1-0ubuntu0.11.10.1_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 10.0.2+build1-0ubuntu0.11.10.1 (using .../firefox-gnome-support_11.0+build1-0ubuntu0.11.10.1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 10.0.2+build1-0ubuntu0.11.10.1 (using .../firefox-locale-en_11.0+build1-0ubuntu0.11.10.1_all.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace libnautilus-extension1 1:3.2.1-0ubuntu4.1 (using .../libnautilus-extension1_1%3a3.2.1-0ubuntu4.2_i386.deb) ...
Unpacking replacement libnautilus-extension1 ...
Preparing to replace nautilus-data 1:3.2.1-0ubuntu4.1 (using .../nautilus-data_1%3a3.2.1-0ubuntu4.2_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.2.1-0ubuntu4.1 (using .../nautilus_1%3a3.2.1-0ubuntu4.2_i386.deb) ...
Unpacking replacement nautilus ...
Preparing to replace xul-ext-ubufox 1.0.2-0ubuntu0.11.10.1 (using .../xul-ext-ubufox_1.0.3-0ubuntu1_all.deb) ...
Unpacking replacement xul-ext-ubufox ...
Processing triggers for software-center ...
Updating software catalog...this may take a moment.
Software catalog update was successful.
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Setting up ttf-mscorefonts-installer (3.3ubuntu4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2012-03-19 19:02:29--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2012-03-19 19:02:30--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://kent.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://kent.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2012-03-19 19:02:30--  [http://kent.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://kent.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

     0K .......... .......... .......... .......... .......... 25%  422K 0s
    50K .......... .......... .......... .......... .......... 51%  839K 0s
   100K .......... .......... .......... .......... .......... 77% 1022K 0s
   150K .......... .......... .......... .......... ...       100%  339K=0.4s

2012-03-19 19:02:30 (544 KB/s) - `./andale32.exe' saved [198384/198384]

--2012-03-19 19:02:31--  [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2012-03-19 19:02:31--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2012-03-19 19:02:31--  [http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/x-msdos-program]
Saving to: `./arialb32.exe'

     0K .......... .......... .......... .......... .......... 30%  645K 0s
    50K .......... .......... .......... .......... .......... 60%  939K 0s
   100K .......... .......... .......... .......... .......... 91%  451K 0s
   150K .......... ....                                       100%  456K=0.3s

2012-03-19 19:02:32 (602 KB/s) - `./arialb32.exe' saved [168176/168176]

--2012-03-19 19:02:32--  [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2012-03-19 19:02:32--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2012-03-19 19:02:32--  [http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Resolving freefr.dl.sourceforge.net... 88.191.250.132
Connecting to freefr.dl.sourceforge.net|88.191.250.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/x-msdownload]
Saving to: `./arial32.exe'

     0K .......... .......... .......... .......... ..........  9%  229K 2s
    50K .......... .......... .......... .......... .......... 18%  605K 1s
   100K .......... .......... .......... .......... .......... 27% 1.44M 1s
   150K .......... .......... .......... .......... .......... 36%  473K 1s
   200K .......... .......... .......... .......... .......... 46% 1.61M 1s
   250K .......... .......... .......... .......... .......... 55%  545K 0s
   300K .......... .......... .......... .......... .......... 64% 1022K 0s
   350K .......... .......... .......... .......... .......... 73%  828K 0s
   400K .......... .......... .......... .......... .......... 83% 1.19M 0s
   450K .......... .......... .......... .......... .......... 92%  853K 0s
   500K .......... .......... .......... .......... .         100%  722K=0.8s

2012-03-19 19:02:33 (653 KB/s) - `./arial32.exe' saved [554208/554208]

--2012-03-19 19:02:33--  [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2012-03-19 19:02:34--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2012-03-19 19:02:34--  [http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.248.253, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|194.95.248.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/x-msdos-program]
Saving to: `./comic32.exe'

     0K .......... .......... .......... .......... .......... 20%  175K 1s
    50K .......... .......... .......... .......... .......... 41%  744K 0s
   100K .......... .......... .......... .......... .......... 62%  559K 0s
   150K .......... .......... .......... .......... .......... 83%  489K 0s
   200K .......... .......... .......... ..........           100%  497K=0.6s

2012-03-19 19:02:35 (384 KB/s) - `./comic32.exe' saved [246008/246008]

--2012-03-19 19:02:35--  [http://downloads.sourceforge.net/corefonts/courie32.exe](http://downloads.sourceforge.net/corefonts/courie32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2012-03-19 19:02:35--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2012-03-19 19:02:36--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Resolving garr.dl.sourceforge.net... 193.206.140.34, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|193.206.140.34|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/octet-stream]
Saving to: `./courie32.exe'

     0K .......... .......... .......... .......... ..........  7%  235K 2s
    50K .......... .......... .......... .......... .......... 15%  582K 2s
   100K .......... .......... .......... .......... .......... 23%  801K 1s
   150K .......... .......... .......... .......... .......... 31%  681K 1s
   200K .......... .......... .......... .......... .......... 39%  403K 1s
   250K .......... .......... .......... .......... .......... 47% 3.53M 1s
   300K .......... .......... .......... .......... .......... 55%  528K 1s
   350K .......... .......... .......... .......... .......... 63%  406K 0s
   400K .......... .......... .......... .......... .......... 71%  369K 0s
   450K .......... .......... .......... .......... .......... 79% 16.2M 0s
   500K .......... .......... .......... .......... .......... 87% 1.19M 0s
   550K .......... .......... .......... .......... .......... 95%  516K 0s
   600K .......... .......... .......... .                    100%  592K=1.1s

2012-03-19 19:02:37 (564 KB/s) - `./courie32.exe' saved [646368/646368]

--2012-03-19 19:02:37--  [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2012-03-19 19:02:38--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2012-03-19 19:02:38--  [http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://heanet.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/x-msdos-program]
Saving to: `./georgi32.exe'

     0K .......... .......... .......... .......... .......... 13%  421K 1s
    50K .......... .......... .......... .......... .......... 26%  496K 1s
   100K .......... .......... .......... .......... .......... 39%  529K 0s
   150K .......... .......... .......... .......... .......... 52%  806K 0s
   200K .......... .......... .......... .......... .......... 65%  576K 0s
   250K .......... .......... .......... .......... .......... 78%  461K 0s
   300K .......... .......... .......... .......... .......... 91%  889K 0s
   350K .......... .......... .......... ...                  100%  458K=0.7s

2012-03-19 19:02:39 (547 KB/s) - `./georgi32.exe' saved [392440/392440]

--2012-03-19 19:02:39--  [http://downloads.sourceforge.net/corefonts/impact32.exe](http://downloads.sourceforge.net/corefonts/impact32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2012-03-19 19:02:39--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2012-03-19 19:02:39--  [http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Resolving ignum.dl.sourceforge.net... 62.109.128.11, 2001:1ab0:7e1f:1:230:48ff:fed1:9c0a
Connecting to ignum.dl.sourceforge.net|62.109.128.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/x-msdownload]
Saving to: `./impact32.exe'

     0K .......... .......... .......... .......... .......... 29%  306K 0s
    50K .......... .......... .......... .......... .......... 59%  792K 0s
   100K .......... .......... .......... .......... .......... 88%  640K 0s
   150K .......... .........                                  100% 1.73M=0.3s

2012-03-19 19:02:40 (536 KB/s) - `./impact32.exe' saved [173288/173288]

--2012-03-19 19:02:40--  [http://downloads.sourceforge.net/corefonts/times32.exe](http://downloads.sourceforge.net/corefonts/times32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2012-03-19 19:02:40--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2012-03-19 19:02:40--  [http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/x-msdos-program]
Saving to: `./times32.exe'

     0K .......... .......... .......... .......... ..........  7%  339K 2s
    50K .......... .......... .......... .......... .......... 15%  823K 1s
   100K .......... .......... .......... .......... .......... 23%  439K 1s
   150K .......... .......... .......... .......... .......... 30%  685K 1s
   200K .......... .......... .......... .......... .......... 38%  784K 1s
   250K .......... .......... .......... .......... .......... 46%  545K 1s
   300K .......... .......... .......... .......... .......... 54% 1.30M 0s
   350K .......... .......... .......... .......... .......... 61%  689K 0s
   400K .......... .......... .......... .......... .......... 69%  569K 0s
   450K .......... .......... .......... .......... .......... 77% 3.93M 0s
   500K .......... .......... .......... .......... .......... 85%  480K 0s
   550K .......... .......... .......... .......... .......... 92%  734K 0s
   600K .......... .......... .......... .......... ......    100% 8.33M=0.9s

2012-03-19 19:02:42 (688 KB/s) - `./times32.exe' saved [661728/661728]

--2012-03-19 19:02:42--  [http://downloads.sourceforge.net/corefonts/trebuc32.exe](http://downloads.sourceforge.net/corefonts/trebuc32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2012-03-19 19:02:42--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2012-03-19 19:02:42--  [http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://ignum.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving ignum.dl.sourceforge.net... 62.109.128.11, 2001:1ab0:7e1f:1:230:48ff:fed1:9c0a
Connecting to ignum.dl.sourceforge.net|62.109.128.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/x-msdownload]
Saving to: `./trebuc32.exe'

     0K .......... .......... .......... .......... .......... 14%  369K 1s
    50K .......... .......... .......... .......... .......... 28%  839K 0s
   100K .......... .......... .......... .......... .......... 43%  497K 0s
   150K .......... .......... .......... .......... .......... 57% 4.25M 0s
   200K .......... .......... .......... .......... .......... 71%  560K 0s
   250K .......... .......... .......... .......... .......... 86%  514K 0s
   300K .......... .......... .......... .......... ........  100% 53.1M=0.5s

2012-03-19 19:02:43 (705 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2012-03-19 19:02:43--  [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2012-03-19 19:02:43--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2012-03-19 19:02:44--  [http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://dfn.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.248.253, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|194.95.248.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/x-msdos-program]
Saving to: `./verdan32.exe'

     0K .......... .......... .......... .......... .......... 14%  221K 1s
    50K .......... .......... .......... .......... .......... 29%  449K 1s
   100K .......... .......... .......... .......... .......... 43%  684K 1s
   150K .......... .......... .......... .......... .......... 58%  446K 0s
   200K .......... .......... .......... .......... .......... 72%  893K 0s
   250K .......... .......... .......... .......... .......... 87%  863K 0s
   300K .......... .......... .......... .......... ...       100%  516K=0.7s

2012-03-19 19:02:45 (476 KB/s) - `./verdan32.exe' saved [351992/351992]

--2012-03-19 19:02:45--  [http://downloads.sourceforge.net/corefonts/webdin32.exe](http://downloads.sourceforge.net/corefonts/webdin32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2012-03-19 19:02:45--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2012-03-19 19:02:45--  [http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://switch.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/x-msdos-program]
Saving to: `./webdin32.exe'

     0K .......... .......... .......... .......... .......... 27%  327K 0s
    50K .......... .......... .......... .......... .......... 55%  427K 0s
   100K .......... .......... .......... .......... .......... 82%  521K 0s
   150K .......... .......... ..........                      100% 1.16M=0.4s

2012-03-19 19:02:46 (461 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: OK
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: OK
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: OK
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: OK
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: OK
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: OK
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: OK
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: OK
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: OK
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: OK
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: OK
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
Setting up language-pack-en (1:11.10+20120306) ...
Setting up language-pack-gnome-en (1:11.10+20120306) ...
Setting up app-install-data-partner (12.11.10.2) ...
Setting up firefox (11.0+build1-0ubuntu0.11.10.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (11.0+build1-0ubuntu0.11.10.1) ...
Setting up firefox-gnome-support (11.0+build1-0ubuntu0.11.10.1) ...
Setting up firefox-locale-en (11.0+build1-0ubuntu0.11.10.1) ...
Setting up libnautilus-extension1 (1:3.2.1-0ubuntu4.2) ...
Setting up nautilus-data (1:3.2.1-0ubuntu4.2) ...
Setting up nautilus (1:3.2.1-0ubuntu4.2) ...
Setting up xul-ext-ubufox (1.0.3-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
michael@michael-ThinkPad-X31:~$ 
```

Hope this helps.

---

### Post by raja.genupula on 2012-03-19
new updates are installed with out any problem . 
have you tried installing other software i mean something like VLC media player or something else .

---

### Post by Hookheathen on 2012-03-20
Thanks your help. The problem has seeming resolved itself and the updates have loaded on fine. No more error message.

---

### Post by raja.genupula on 2012-03-20
Thats great news , please mark the thread as solved from thread tools . 

Thank you .

---

