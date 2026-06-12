---
title: "hash sum mismatch , unable to update"
date: 2010-04-12
forum: General Help
---

### Post by Shpongle on 2010-04-12
Hey all , Over the last few days I have been unable to upgrade , I keep getting a hash sum mismatch error. Im using karmic

dill@default:~$ sudo apt-get upgrade && sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  chromium-browser erlang-base erlang-crypto erlang-inets erlang-mnesia
  erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools
  erlang-xmerl firefox firefox-branding firefox-gnome-support ifupdown
  libnss3-1d libnss3-dev libwebkit-1.0-2 obexd-client xulrunner-1.9.1
  xulrunner-1.9.1-dev
20 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.1MB/48.9MB of archives.
After this operation, 4,424kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic-updates/main libnss3-dev 3.12.6-0ubuntu0.9.10.2 [261kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main chromium-browser 5.0.372.0~svn20100409r44042-0ubuntu1~ucd1~karmic [12.2MB]
Get:3 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic-updates/main libnss3-1d 3.12.6-0ubuntu0.9.10.2 [1,120kB]
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic-updates/main ifupdown 0.6.8ubuntu21.2 [58.2kB]
Get:5 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic-updates/main erlang-base 1:13.b.1-dfsg-2ubuntu1.1 [3,479kB]
Get:6 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic-updates/main obexd-client 0.14-0ubuntu1.1 [53.3kB]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main firefox 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~karmic [11.3MB]
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libwebkit-1.0-2 1.2.0-1~karmic1 [5,120kB]
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main xulrunner-1.9.1-dev 1.9.1.10~hg20100410r26879+nobinonly-0ubuntu1~umd1~karmic [5,285kB]
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main xulrunner-1.9.1 1.9.1.10~hg20100410r26879+nobinonly-0ubuntu1~umd1~karmic [8,290kB]
Fetched 47.1MB in 10min 2s (78.2kB/s)                                          
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.2_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.2_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_5.0.372.0~svn20100409r44042-0ubuntu1~ucd1~karmic_i386.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_5.0.372.0~svn20100409r44042-0ubuntu1~ucd1~karmic_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-base_13.b.1-dfsg-2ubuntu1.1_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-base_13.b.1-dfsg-2ubuntu1.1_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox/firefox_3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~karmic_i386.deb](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/f/firefox/firefox_3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1~karmic_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/suraia/ppa/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.0-1~karmic1_i386.deb](http://ppa.launchpad.net/suraia/ppa/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.0-1~karmic1_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-dev_1.9.1.10~hg20100410r26879+nobinonly-0ubuntu1~umd1~karmic_i386.deb](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-dev_1.9.1.10~hg20100410r26879+nobinonly-0ubuntu1~umd1~karmic_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.10~hg20100410r26879+nobinonly-0ubuntu1~umd1~karmic_i386.deb](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.10~hg20100410r26879+nobinonly-0ubuntu1~umd1~karmic_i386.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
dill@default:~$ 


I have tried running it with fix- missing ,  also tried clearing the cache and checked my sources list too


heres my sources list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/suraia/ppa/ubuntu](http://ppa.launchpad.net/suraia/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/suraia/ppa/ubuntu](http://ppa.launchpad.net/suraia/ppa/ubuntu) karmic main



anyone have any ideas ?

---

### Post by plucky on 2010-04-13
Go [Here](http://repogen.simplylinux.ch/) and generate yourself a proper sources.list.You seem to have a lot of third party repositories but none of the Ubuntu restricted,main,universe and multiverse repositories.

Then run ```
sudo apt-get update
``` to reload the index files and ```
sudo apt-get upgrade
``` to actually install the updates.


Good Luck

---

### Post by Shpongle on 2010-04-13
Thanks for the reply , I keep getting  Sub-process /bin/bzip2 returned an error code (2)  any ideas ?, I cant seem to find much about it on google. Anybody have any suggestions ?


dill@default:~$ sudo apt-get update
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/main Translation-en_IE                                                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                                                                                                                           
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IE                                                                                                             
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/restricted Translation-en_IE                                                                                                          
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/universe Translation-en_IE                                                                                      
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/multiverse Translation-en_IE                                                                                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic Release                                                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                                                                               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                                
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_IE                           
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                                       
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_IE                              
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-en_IE                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_IE                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                                                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/main Packages                                           
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                              
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/restricted Packages                                  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/universe Packages                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/multiverse Packages              
Get:5 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/main Sources [640kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                                                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                                                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                                                                    
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [3,392B]                                    
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [1,396B]                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                                                                      
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                                 
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [16.2kB]
Get:9 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/restricted Sources [3,270B]
Get:10 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/universe Sources [2,795kB]
22% [5 Sources bzip2 0] [10 Sources 14192/2,795kB 0%]
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/main Sources 
  Sub-process /bin/bzip2 returned an error code (2)
Get:11 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/multiverse Sources [116kB]        
99% [10 Sources bzip2 958464]                                                
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 3,707kB in 6s (601kB/s)                                                                                                                                                    
W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Shpongle on 2010-04-13
I got it to work now by doing a fresh source list and verifying them , but for some reason it will not work with the chromium ppa and or the webupd8 ppa for the light themes. they keep giving me hash sum mismatch errors 

i have removed them and it works and when i re add them i get errors ?? ,  

such as this


dill@default:~$ sudo apt-get update && sudo apt-get upgradeHit 
[http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/main Translation-en_IE                 
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/restricted Translation-en_IE           
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/universe Translation-en_IE             
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/multiverse Translation-en_IE           
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IE                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/main Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_IE             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-en_IE            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) karmic/multiverse Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_IE
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_IE
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  firefox firefox-branding firefox-gnome-support xulrunner-1.9.1
  xulrunner-1.9.1-dev
The following packages will be upgraded:
  humanity-icon-theme
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 3,647kB of archives.
After this operation, 1,606kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main humanity-icon-theme 0.5.2-1~webupd8~karmic [3,647kB]
Fetched 3,647kB in 34s (105kB/s)                                               
Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/h/humanity-icon-theme/humanity-icon-theme_0.5.2-1~webupd8~karmic_all.deb](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/h/humanity-icon-theme/humanity-icon-theme_0.5.2-1~webupd8~karmic_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by tzg6sa on 2010-05-09
I got the very same error. I could not install anything for a few days. I have a one week old fresh install on my machine, so it is not upgrade-related. Any other idea?

---

