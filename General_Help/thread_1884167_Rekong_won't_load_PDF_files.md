---
title: "Rekong won't load PDF files"
date: 2011-11-20
forum: General Help
---

### Post by tropdoug on 2011-11-20
Since Firefox has dropped a lot of its support for variousa features I am trying Rekong. However I need to download a statement in pdf format and it tells me I need adobe reader plugin. 

2 questions -- 

Why will this document not use Okular which is set to open from rekong?

If I do need Adobe -- where can I get a 64 bit version for linux, because it does not appear on their download page?

supplementary question -- How do I get the Home icon to show to the left of the address bar? In the help document it shows it, but it is not on my browser. 

Thanks for any help.

---

### Post by dniMretsaM on 2011-11-20
You might try [FONT=Courier New]kpartsplugin[/FONT]. It allows you to view a ton of different document types within the browser. I don't know if it works in Rekonq or not though (I use Firefox).

---

### Post by tropdoug on 2011-11-21
installed kparts - no difference. 

I am maybe getting more stupid with age, I found the 64 bit version of flash, downloaded it. It is a tar.gz file. I cannot find out how to install it! There is no read me or installation instruction within the archive and nothing that I can find on the net. 

Why is this so difficult?

After 4 years I feel I am being pushed back to windows solely due to the lack of information about finding and installing the required applications that are standard in windows and mac to make there apps fully functional. 

I am a user of Linux not a developer or tech geek, and I think it is about time the developers realised the need to address this issue.

Any help anyone? please.

---

### Post by dniMretsaM on 2011-11-21
You don't want kparts, you want kpartsplugin. Those are two different packages. And what features are you missing in Firefox? As for installing from a .tar.gz file, there are tons of sites that have information on this, but it's not necessary. I recommend installing it though through the USC, using Flash-Aid (Firefox plugin), or downloading the Ubuntu package from the Adobe site.

---

### Post by tropdoug on 2011-11-22
Thanks -- Kpartsplugin does not appear in synaptics or in kde package manager?? 

Firefox no longer supports google toolbar in 64 bit version and although I used the installed (by default) "Mozilla Firefox Browser Installer" nothing happens - it does not install firefox.

Using the instructions I have found of unpacking the tarball cd to its new directory and using ./configure ./make install and ./install does not work because there are no shell scripts included in the download packages. I am not sufficiently "system knowleadgable to proceed further without help, but I have spent 5 days trying very hard to find the informatioin and apply it before I posted. 

As to  Bodhi.Zazen's comment I am always and have frequently praised the work of developers that are enabling people like me to experience the much better OS of linux. 

However if the attitude is that before someone can comment on issues which are causing frustration and probably turning some people back to Winblows, you have to be a coder is somewhat churlish not to mention plain silly.Linux has been growing for many years precisely because it has been answering the needs of many people like me --- users of the system for fun and work productivity. 

Ubuntu failed this with Unity and heaps of otherwise satisfied users are turning to other OS's. For me KDE is also failing in that I can not get programs that worked fine in previous distro's of KDE to work on this one. I understand that with Firefox that has nothing to do with the KDE Developers, but with the other issues it does. So I stand by my frustrated view.

If someone can instruct me on how to installe firefox with the current download verison for 64 bit OS's from their site, I would be very grateful. Ditto if I can get instructions on Rekonq (which doesn't even match the screenshots of the browser in its documentation) 

Something I do at work is called Quality Assurance in Documents. When a new version of a form, document, work instruction etc comes out, it is not allowed to be released until people like me have updated all the instances of help documents, links and web sites, hard drive heirarchies and instructions, so that users always have the correct information at their fingertips. If I could be of assistance to the KDE community in this regard I would love to give of my time, but I have to know how and where to start. Any suggestions?

Please feel my pain as I feel your love -- Linux is good, it could be better, and it is getting there and will always be getting there -- especially when those with the know how help those without it. 

I hope that my message and my genuine request for help is responded too positively. 

Douglas

---

### Post by dniMretsaM on 2011-11-22
That's odd. I don't know why it isn't appearing in synaptic. I'll do some digging and see what I can find. I would just install Firefox from the repos (Synaptic, KPackageKit,  Muon, etc.). You also might want to use  [this  PPA](https://launchpad.net/~mozillateam/+archive/firefox-stable) (assuming your on 10.10 like your mini-profile says. If your  on 11.xx, you don't need the PPA) so you can use FF8. If you're  comfortable with the command line, you can run these:

Add the PPA (again, if you're not on 11.xx):
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

To install Firefox:
```
sudo apt-get update 
sudo apt-get install firefox
```

For installing Flash, you can use the Firefox  add-on [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) (probably the easiest option). Or you  could download the  [64-bit  .deb package](http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_11_for_Ubuntu_%28apt%29) from Adobe and install it through GDebi (pre-11.10)  or QApt (11.10). I'll do some looking around and see what I can find on  using your particular skills to help out (will be documentation related,  I'm pretty sure).

---

### Post by oldos2er on 2011-11-22
> **tropdoug said:**
> Thanks -- Kpartsplugin does not appear in synaptics or in kde package manager??

Can you run ```
sudo apt-get update && sudo apt-get install kpartsplugin
``` in a konsole and post the output here?

---

### Post by tropdoug on 2011-11-23
Thanks guys.

The output from the command given is 

```
douglas@VN900:~$ sudo apt-get update && sudo apt-get install kpartsplugin
[sudo] password for douglas: 
Ign http://au.archive.ubuntu.com natty InRelease
Ign http://au.archive.ubuntu.com natty-updates InRelease                       
Get:1 http://mirror.optus.net sid InRelease [160 kB]                           
Hit http://au.archive.ubuntu.com natty Release.gpg                             
Get:2 http://au.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Hit http://au.archive.ubuntu.com natty Release                                 
Get:3 http://au.archive.ubuntu.com natty-updates Release [31.4 kB]             
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://mirror.optus.net sid InRelease                                      
Get:4 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Hit http://au.archive.ubuntu.com natty/main Sources                            
Hit http://au.archive.ubuntu.com natty/restricted Sources                      
Hit http://au.archive.ubuntu.com natty/universe Sources                        
Hit http://au.archive.ubuntu.com natty/multiverse Sources                      
Hit http://au.archive.ubuntu.com natty/main amd64 Packages                     
Get:5 http://mirror.optus.net sid/main Sources/DiffIndex [2,038 B]             
Hit http://au.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://au.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://au.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://au.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://au.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://au.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://au.archive.ubuntu.com natty/universe TranslationIndex               
Get:6 http://au.archive.ubuntu.com natty-updates/main Sources [141 kB]         
Get:7 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Hit http://archive.canonical.com natty Release.gpg                             
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release                                     
Get:8 http://mirror.optus.net sid/main amd64 Packages/DiffIndex [2,038 B]      
Get:9 http://au.archive.ubuntu.com natty-updates/restricted Sources [753 B]    
Get:10 http://au.archive.ubuntu.com natty-updates/universe Sources [33.0 kB]   
Get:11 http://au.archive.ubuntu.com natty-updates/multiverse Sources [2,317 B] 
Get:12 http://au.archive.ubuntu.com natty-updates/main amd64 Packages [411 kB] 
Get:13 http://security.ubuntu.com natty-security Release [31.4 kB]             
Hit http://archive.canonical.com natty Release                                 
Get:14 http://mirror.optus.net sid/main TranslationIndex [2,045 B]             
Hit http://extras.ubuntu.com natty/main Sources                                
Get:15 http://mirror.optus.net sid/main 2011-11-22-0815.16.pdiff [6,062 B]     
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:16 http://mirror.optus.net sid/main amd64 2011-11-22-0815.16.pdiff [9,253 B]
Get:17 http://mirror.optus.net sid/main 2011-11-22-0815.16.pdiff [6,062 B]     
Get:18 http://mirror.optus.net sid/main amd64 2011-11-22-0815.16.pdiff [9,253 B]
Ign http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:19 http://mirror.optus.net sid/main 2011-11-22-1412.22.pdiff [10.3 kB]     
Get:20 http://mirror.optus.net sid/main 2011-11-22-1412.22.pdiff [10.3 kB]     
Get:21 http://au.archive.ubuntu.com natty-updates/restricted amd64 Packages [838 B]
Get:22 http://au.archive.ubuntu.com natty-updates/universe amd64 Packages [119 kB]
Get:23 http://mirror.optus.net sid/main amd64 2011-11-22-1412.22.pdiff [5,980 B]
Get:24 http://mirror.optus.net sid/main amd64 2011-11-22-1412.22.pdiff [5,980 B]
Get:25 http://mirror.optus.net sid/main 2011-11-22-2021.23.pdiff [10.6 kB]     
Get:26 http://au.archive.ubuntu.com natty-updates/multiverse amd64 Packages [4,997 B]
Ign http://au.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://au.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://au.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://au.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://au.archive.ubuntu.com natty/main Translation-en_AU                  
Hit http://au.archive.ubuntu.com natty/multiverse Translation-en_AU            
Hit http://au.archive.ubuntu.com natty/restricted Translation-en_AU            
Get:27 http://mirror.optus.net sid/main 2011-11-22-2021.23.pdiff [10.6 kB]     
Get:28 http://mirror.optus.net sid/main amd64 2011-11-22-2021.23.pdiff [18.5 kB]
Ign http://au.archive.ubuntu.com natty/main Translation-en                     
Ign http://au.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://au.archive.ubuntu.com natty/restricted Translation-en               
Ign http://au.archive.ubuntu.com natty/universe Translation-en_AU              
Ign http://au.archive.ubuntu.com natty/universe Translation-en                 
Ign http://au.archive.ubuntu.com natty-updates/main Translation-en_AU          
Ign http://au.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://au.archive.ubuntu.com natty-updates/multiverse Translation-en_AU    
Get:29 http://mirror.optus.net sid/main amd64 2011-11-22-2021.23.pdiff [18.5 kB]
Ign http://au.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://au.archive.ubuntu.com natty-updates/restricted Translation-en_AU    
Ign http://au.archive.ubuntu.com natty-updates/restricted Translation-en       
Get:30 http://mirror.optus.net sid/main 2011-11-23-0213.06.pdiff [8,368 B]     
Ign http://au.archive.ubuntu.com natty-updates/universe Translation-en_AU      
Ign http://au.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://extras.ubuntu.com natty/main Translation-en_AU                      
Get:31 http://security.ubuntu.com natty-security/main Sources [81.5 kB]        
Ign http://archive.canonical.com natty/partner Translation-en_AU               
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:32 http://mirror.optus.net sid/main 2011-11-23-0213.06.pdiff [8,368 B]     
Get:33 http://mirror.optus.net sid/main amd64 2011-11-23-0213.06.pdiff [6,503 B]
Ign http://archive.canonical.com natty/partner Translation-en                  
Get:34 http://mirror.optus.net sid/main amd64 2011-11-23-0213.06.pdiff [6,503 B]
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages                         
  404  Not Found
Get:35 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:36 http://security.ubuntu.com natty-security/universe Sources [14.4 kB]    
Ign http://ppa.launchpad.net natty/main Translation-en_AU                      
Get:37 http://security.ubuntu.com natty-security/multiverse Sources [652 B]    
Get:38 http://security.ubuntu.com natty-security/main amd64 Packages [253 kB]  
Ign http://ppa.launchpad.net natty/main Translation-en                         
Get:39 http://security.ubuntu.com natty-security/restricted amd64 Packages [14 B]
Get:40 http://security.ubuntu.com natty-security/universe amd64 Packages [57.5 kB]
Get:41 http://security.ubuntu.com natty-security/multiverse amd64 Packages [1,935 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://security.ubuntu.com natty-security/main Translation-en_AU           
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_AU
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_AU
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_AU
Ign http://security.ubuntu.com natty-security/universe Translation-en
Fetched 1,428 kB in 1min 4s (22.1 kB/s)
W: GPG error: http://mirror.optus.net sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
douglas@VN900:~$ 

```

There are some PPA's in there that failed. These were one of the attempts to download something supposed to help the issues but the information was inaccurate.

---

### Post by dniMretsaM on 2011-11-23
You should remove those PPA's. Depending on how you added them, they are either in /etc/apt/sources.list or /etc/apt/sources.list.d/ I would recommend removing them through a package management GUI, though. Less chance of creating problems that way.

Run this (when you ran the command oldos2er gave you the second part didn't run due to the PPA failure):
```
sudo apt-get install kpartsplugin
```

---

### Post by tropdoug on 2011-11-26
OK I have firefox finally installed. But flash does not play. There are errors that I dion't know howto resolve.

```
Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
Setting up firefox (8.0+build1-0ubuntu0.11.04.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (8.0+build1-0ubuntu0.11.04.3) ...
Setting up xul-ext-ubufox (0.9.2-0ubuntu0.11.04.2) ...
Setting up ubufox (0.9.2-0ubuntu0.11.04.2) ...
Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
douglas@VN900:~$
```

---

### Post by dniMretsaM on 2011-11-26
> **tropdoug said:**
> OK I have firefox finally installed. But flash does not play. There are errors that I dion't know howto resolve.

```
Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
Setting up firefox (8.0+build1-0ubuntu0.11.04.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (8.0+build1-0ubuntu0.11.04.3) ...
Setting up xul-ext-ubufox (0.9.2-0ubuntu0.11.04.2) ...
Setting up ubufox (0.9.2-0ubuntu0.11.04.2) ...
Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
douglas@VN900:~$
```

Have you tried Flash-Aid?

---

### Post by tropdoug on 2011-12-03
Thanks for all the help. I have found a solution (sort of). I decided to install 11.10 (kde) and bingo rekonq and firefox both worked "out of the box" so to speak. full flash intergration noissues. Seems weird but there we go. 

So once again please accept my thanks. I do have another problem but I will start a new thread for that one. :-)

---

