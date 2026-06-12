---
title: "Daily update list size is killing me."
date: 2012-05-03
forum: General Help
---

### Post by skew on 2012-05-03
For us poor slobs who STILL have no choice but to use dial-up, due to where we live. The 15-22mb download required to refresh the update list everyday is untenable, at best.

   This appears to be a recent phenomena. Is there something new going on with the update system (bug, software change, etc)? I did'nt have this problem until about a month or so ago. From what I've read on another forum (thats now closed) I'm not the only person who's experiencing this.

[http://ubuntuforums.org/showthread.php?t=1964421&highlight=apt-get+download+all+list+everyday+lists+huge](http://ubuntuforums.org/showthread.php?t=1964421&highlight=apt-get+download+all+list+everyday+lists+huge)

  Is their any other options available to keep on top of security updates without this drawn out daily download? Currently it can take an hour to an hour and a half to download the lists. I've used both the CL 'apt-get update' and the Update-Manager with the same results. From what I can see the lists are usually the same in size and content from the lists download from the day before. the only change which I can find being that the /var/lib/apt/periodic/update-success-stamp  date has changed.  

Any thoughts? 

Thanks!

---

### Post by raja.genupula on 2012-05-03
have you tried in terminal ?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

after doing these commands in your terminal , open the GUI update manager and let us know what its giving to you .

all the best.

---

### Post by Zill on 2012-05-03
> **skew said:**
> ...Any thoughts?...
As each new release of Ubuntu comes out it is generally both preceded and  followed by a period of intense activity as the bugs are identified and squashed, inevitably resulting in loads of updates.

If you want to minimise the number of updates then I suggest you do not install the "latest and greatest" immediately it is released but, instead, wait a while for the release to settle down to a *relatively* stable state with fewer updates.

Following this to its logical conclusion, there is a lot to be said for sticking to older, but still supported, releases such as Lucid 10.04 - my current Ubuntu release. ;-)

---

### Post by vasa1 on 2012-05-03
Make sure you you untick "source code" in Software Sources. That will help a bit.

---

### Post by skew on 2012-05-03
When I get the TIME to wait through another list update I will try out the suggestions above. In the mean time heres some additional info.

The problems started a month or so ago with ver 11.10. Oneiric. If the issue was just related to 12.04 why am I seeing it with 11.10 as well? 
I may be wrong but I think I recall that there was an update to "apt-get" or "synaptic", etc back then. My history doesn't go back that far so I can't be sure.    

  Yesterday I installed 12.04 on another system to check out. I updated the lists with the update manager last night. It took an expectedly long period of time to grab the first batch of lists, this I expected.  After I wrote the OP I went on that system and updated the lists again with the update manager. Less then 18 hours since the last list update and it took an hour and 10 minutes to grab 19mb of lists again. 

  IMO, This process should be more discrete, like a patch to an exisiting list, not a complete reloading of all the lists just because a few programs may have had changes implemented. Its a horrible waste of time and bandwidth.

   I am still left with the question. Can I just download the updated security lists alone?  As I assume from looking at their list size, doing so would be a quicker download.

 If I can't find a soultion I will have no choice but to search out a distro which is more bandwidth friendly and better suited to dialup use.  

Thanks again.

---

### Post by skew on 2012-05-03
> **raja.genupula said:**
> have you tried in terminal ?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

after doing these commands in your terminal , open the GUI update manager and let us know what its giving to you .

all the best.

I did as you requested using ver 11.10. I also unchecked downloading the source code lists as vasa1 had suggested.

 apt-get update downloaded 12mb (which is smaller I assume because of not downloading the source code lists. Still it took 45 minutes). There was nothing to apt-get upgrade.  apt-get dist-upgrade did nothing significant.

 I then started update manager. It stated at the top of the window that I had just updated the lists. I clicked on update and it started the process of downloading all the lists that i'd just updated minutes before again. After five minutes of watching the terminal output to be sure of this, I gave up, pressed cancel and got off of this (not so)merry-go-round, and hung up. 

Does this tell you anything? What now?  

Thanks

---

### Post by skew on 2012-05-03
It's something of a hacket job and only addresses part of the issue. However... with the following I can now just update the security lists alone. FWIW. I dug this up, in part, elsewhere on the web. My list update size download went from 12mb to just over 300kb.


sudo cp /etc/apt/sources.list /etc/apt/security.sources.list

Edit the latter to contain only security repositories, then:

sudo apt-get update -o Dir::Etc::SourceList=/etc/apt/security.sources.list

then

sudo apt-get upgrade -o Dir::Etc::SourceList=/etc/apt/security.sources.list

Build a bash script to house it and let fly.


This still leaves the other matter of huge lists which have to be downloaded in their entirety whenever the 'check for updates' button is pressed. 

Feels like a bug to me.

---

### Post by CharlesA on 2012-05-03
Thanks for the tip. I was wondering why there was a boatload of stuff that needed "updating" after doing an apt-get update.

---

### Post by brad1138 on 2012-05-03
You should really look into this: ["Exede.com"]("http://get.exede.com/") The new satellite internet, launched Feb 2012, has been getting 12-25 mbps (12 is base) it is actually quite good. If you happen to live in Western Washington State, I can sell & install it for you  :) (I work at a family owned dealer for Dish, DirecTV & Exede in Olympia WA)

---

### Post by skew on 2012-05-03
> **brad1138 said:**
> You should really look into this: ["Exede.com"]("http://get.exede.com/") The new satellite internet, launched Feb 2012, has been getting 12-25 mbps (12 is base) it is actually quite good. If you happen to live in Western Washington State, I can sell & install it for you  :) (I work at a family owned dealer for Dish, DirecTV & Exede in Olympia WA)

How far out of country will you travel for a house call? :-D

---

### Post by brad1138 on 2012-05-04
> **skew said:**
> How far out of country will you travel for a house call? :-D

Not sure, do you live in the Bahamas? :)

---

### Post by skew on 2012-05-08
The issue remains frustratingly unresolved. :-(

When i just download the security updates alone, in the manner I mention in an earler post, the rest of the lists are deleted and Synaptic then appears strangely empty of applications, libraries, etc. 

  For the last few days I've been tring to find a remedy with no success.

  Again today I updated the normal, universe, multiverse, security lists.
In other words, a typical list update. It took over an hour for both versions 11.10 and 12.04. Immediatly after they are completed, with no updates security or otherwise listed as required, I tried clicking the check updates button again and the whole download process began again as if from scratch. Another hour wasted for each version to give me the same lists it had an hour before just retreived.

 Can someone from Ubuntu (Canonical) tell me if this is normal or a bug in the updating system. If it's the NEW normal then it's time to find another more bandwidth friendly distro and I can stop wasting time on this futile effort. Likewise, if it's a bug, is their any timeline for a fix?

FWIW, I've have also tried using different repositories as well, same issue.

Thanks

---

### Post by Zill on 2012-05-09
> **skew said:**
> ...Again today I updated the normal, universe, multiverse, security lists.
In other words, a typical list update. It took over an hour for both versions 11.10 and 12.04. Immediatly after they are completed, with no updates security or otherwise listed as required, I tried clicking the check updates button again and the whole download process began again as if from scratch. Another hour wasted for each version to give me the same lists it had an hour before just retreived.

 Can someone from Ubuntu (Canonical) tell me if this is normal or a bug in the updating system...
You are unlikely to receive a response from Canonical *unless* you have paid for support.  The rest of the Ubuntu community are simply unpaid volunteers who, collectively, try to help out where we can.

FWIW, I think you have highlighted an important point that is of particular relevance to users who do not have high-speed internet connections.

My understanding is that the current Ubuntu update process is basically that defined by Debian.  As such, I doubt if the Ubuntu community will be able to change something this fundamental.

Having said that, you may like to search for relevant bug reports with both [Ubuntu]("https://bugs.launchpad.net/ubuntu") *and* [Debian]("http://www.debian.org/Bugs/").

If this problem is not currently listed as an active bug then I suggest you may like to [raise a new bug report]("https://help.ubuntu.com/community/ReportingBugs") to initiate work on resolution.

---

### Post by skew on 2012-05-09
> **Zill said:**
> 
FWIW, I think you have highlighted an important point that is of particular relevance to users who do not have high-speed internet connections.

My understanding is that the current Ubuntu update process is basically that defined by Debian.  As such, I doubt if the Ubuntu community will be able to change something this fundamental.



  At the risk of sounding idealistic I thought Ubutnu and OS software in general was more inclusive and less restrictive. I feel that there has been a move away from this egalatarian mean in the last three versions. 

  FWIW I live 20km from the captial city of a G8 country and this location is under serviced for high bandwidth, or even good cell coverage for that matter. Other options, like satellite, exisit but are shockingly overpriced.

  If this is a development trend, and systemic, which it appears to be. I think it is going to hurt everyone, not just the huge constituancy of those who reside in under serviced areas.  I forsee it posing a potential security risk as well. When low bandwidth users give up on updating due to the hassle and time taken to do so, it seem to resaonably follow that it can't help but potentially poses a security risk for everyone. This is only a suppostion on my part, and I could be mistaken on the potential wide ranging consequences. However the risk issues are real for people who are also in my position. As such I can't take that risk, so I'll be checking out other non-Debian based options. 

FWIW, I tried and it's also an issue in linuxmint 12.

Pity really I liked Ubuntu. I never had this issue with Maverick. Which is a version I loved and will dearly miss. RIP!

---

### Post by Enigmapond on 2012-05-09
You might try Apt-Fast. It's for slower connections.:

[http://www.webupd8.org/2010/08/you-can-now-install-apt-fast-from-ppa.html](http://www.webupd8.org/2010/08/you-can-now-install-apt-fast-from-ppa.html)

---

### Post by Zill on 2012-05-09
> **skew said:**
> At the risk of sounding idealistic I thought Ubutnu and OS software in general was more inclusive and less restrictive. I feel that there has been a move away from this egalatarian mean in the last three versions...
You are quite right in that Linux OS's *are* more inclusive and less restrictive.  That is why I gave you links so that you, as a user, are fully empowered to investigate and, if necessary, initiate a bug report to help resolve a problem you have identified.

FOSS *relies* on "the community" (i.e. users like us) to create and mould our software the way we like it.  Any help you can give with this will be much appreciated.

---

### Post by vasa1 on 2012-05-09
> **Enigmapond said:**
> You might try Apt-Fast. It's for slower connections.:

[http://www.webupd8.org/2010/08/you-can-now-install-apt-fast-from-ppa.html](http://www.webupd8.org/2010/08/you-can-now-install-apt-fast-from-ppa.html)

And this forum has at least one thread on it. I use it and like it!

---

### Post by skew on 2012-05-09
> **Zill said:**
> You are quite right in that Linux OS's *are* more inclusive and less restrictive.  That is why I gave you links so that you, as a user, are fully empowered to investigate and, if necessary, initiate a bug report to help resolve a problem you have identified.

FOSS *relies* on "the community" (i.e. users like us) to create and mould our software the way we like it.  Any help you can give with this will be much appreciated.

You're right.

I haven't submitted a bug report yet. I did though check out your links. From the looks of it it appears to be a confusing and daunting process.  Another reasons I haven't is that I thought that it is reserved exclusivly for program flaws(bugs) not for opions on how I or someone else would like a program to work, or am I mistaken?  
 
While i'm at it is their anyone else on dial-up that has also has noticed this as an issue? For that matter has anyone else noticed that everytime they click on the update button all their lists are refreshed from scratch? Even when there is no change in the list that was refreshed from the previous update. Just checking to see if it's a systemic issue.

Now Zill, I will go and delve deeper into your links then I did previously.
Hopefully with some time I can make head or tails out of it all. Thank you again for your asssitance.

**Enigmapond**, Thanks for the fast-apt tip I'll check it out.

---

### Post by Zill on 2012-05-09
> **skew said:**
> I haven't submitted a bug report yet. I did though check out your links. From the looks of it it appears to be a confusing and daunting process.  Another reasons I haven't is that I thought that it is reserved exclusivly for program flaws(bugs) not for opions on how I or someone else would like a program to work, or am I mistaken?...
Writing your first bug report can be confusing but it does eventually make sense.  I suggest the package concerned is "apt-get", as this is the CLI package behind the functionality of the Update Manager GUI.

IMHO, it is very desirable for users to raise bug reports on anything that does not appear to work as expected.  Obviously, we do not all agree on everything!  However, the validity of the bug can only really be discussed once a bug report is in the system.
 
> **skew said:**
> While i'm at it is their anyone else on dial-up that has also has noticed this as an issue? For that matter has anyone else noticed that everytime they click on the update button all their lists are refreshed from scratch? Even when there is no change in the list that was refreshed from the previous update. Just checking to see if it's a systemic issue.
I have just checked my 10.04 (Lucid) system and, although the initial update via the terminal was a 13.1MB download, subsequent runs of the same "sudo apt-get update" command did not involve *any* downloading whatsoever.

Although I use broadband, the speed of the connection should not make an difference.  Therefore it seems your problem must have appeared in Ubuntu releases *after* 10.04.  On this basis, I do suggest you go ahead and raise a bug report on 11.10, the release I understand you have problems with.

The following two links may (or may not!) be of relevance...
[LIST]
[*][Avoiding slow package updates with package diffs]("http://www.debian-administration.org/articles/439")
[*][Are diffs supported when upgrading?]("http://ubuntuforums.org/showthread.php?t=1239711")
[/LIST]

---

### Post by vasa1 on 2012-05-12
@skew and @zill, would you mind looking at [http://askubuntu.com/questions/135818/ubuntu-update-cache-too-big](http://askubuntu.com/questions/135818/ubuntu-update-cache-too-big) and my comment there?

---

### Post by CharlesA on 2012-05-12
> **vasa1 said:**
> @skew and @zill, would you mind looking at [http://askubuntu.com/questions/135818/ubuntu-update-cache-too-big](http://askubuntu.com/questions/135818/ubuntu-update-cache-too-big) and my comment there?
Sounds about right. 

I just did an apt-get update on my server (which has all the deb-src lines commented out) and it didn't need to download anything.

However, on my Precise desktop install with an unmodified sources.list file, I kept having to download 19 megs or so each time I ran an apt-get update:

```
charles@Precise:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Ign http://extras.ubuntu.com precise InRelease 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                   
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:5 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]       
Hit http://extras.ubuntu.com precise Release                                   
Get:6 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://extras.ubuntu.com precise/main Sources                              
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:8 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]     
Get:9 http://security.ubuntu.com precise-security/main Sources [7,089 B]       
Get:10 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:11 http://security.ubuntu.com precise-security/universe Sources [3,653 B]  
Get:12 http://security.ubuntu.com precise-security/multiverse Sources [696 B]  
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [32.9 kB]
Get:14 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:15 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:16 http://security.ubuntu.com precise-security/universe amd64 Packages [8,581 B]
Get:17 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,142 B]
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [32.9 kB]
Get:19 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [8,594 B]
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en     
Hit http://security.ubuntu.com precise-security/restricted Translation-en     
Hit http://security.ubuntu.com precise-security/universe Translation-en       
Ign http://extras.ubuntu.com precise/main Translation-en_US                   
Ign http://extras.ubuntu.com precise/main Translation-en
Get:23 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]
Get:24 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:25 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:26 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:27 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:28 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:29 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:30 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:31 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:32 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:33 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                               
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                         
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                         
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                           
Get:34 http://us.archive.ubuntu.com precise-updates/main Sources [31.2 kB]                                   
Get:35 http://us.archive.ubuntu.com precise-updates/restricted Sources [765 B]                               
Get:36 http://us.archive.ubuntu.com precise-updates/universe Sources [10.1 kB]                               
Get:37 http://us.archive.ubuntu.com precise-updates/multiverse Sources [696 B]                               
Get:38 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [95.2 kB]                            
Get:39 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [757 B]                        
Get:40 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [27.5 kB]                        
Get:41 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,142 B]                      
Get:42 http://us.archive.ubuntu.com precise-updates/main i386 Packages [96.5 kB]                             
Get:43 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]                         
Get:44 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [27.7 kB]                         
Get:45 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]                       
Get:46 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [73 B]                             
Get:47 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [71 B]                       
Get:48 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]                       
Get:49 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [73 B]                         
Get:50 http://us.archive.ubuntu.com precise-backports/main Sources [700 B]                                   
Get:51 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]                              
Get:52 http://us.archive.ubuntu.com precise-backports/universe Sources [1,680 B]                             
Get:53 http://us.archive.ubuntu.com precise-backports/multiverse Sources [14 B]                              
Get:54 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [559 B]                            
Get:55 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                       
Get:56 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [1,387 B]                      
Get:57 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]                       
Get:58 http://us.archive.ubuntu.com precise-backports/main i386 Packages [559 B]                             
Get:59 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                        
Get:60 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [1,391 B]                       
Get:61 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]                        
Get:62 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [71 B]                           
Get:63 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [70 B]                     
Get:64 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                     
Get:65 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [71 B]                       
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                 
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                           
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                           
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                             
Get:66 http://us.archive.ubuntu.com precise-updates/main Translation-en [42.5 kB]                            
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                   
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                   
Get:67 http://us.archive.ubuntu.com precise-updates/universe Translation-en [17.4 kB]                        
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                       
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                 
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                 
Get:68 http://us.archive.ubuntu.com precise-backports/universe Translation-en [696 B]                        
Fetched 19.2 MB in 1min 6s (288 kB/s)                                                                        
Reading package lists... Done
```

After commenting out the deb-src lines, I didn't download anything.
```
charles@Precise:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Ign http://extras.ubuntu.com precise InRelease 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://us.archive.ubuntu.com precise-updates Release.gpg          
Hit http://extras.ubuntu.com precise Release                          
Hit http://us.archive.ubuntu.com precise-backports Release.gpg        
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://extras.ubuntu.com precise/main amd64 Packages             
Hit http://us.archive.ubuntu.com precise Release
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                   
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                     
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                   
Hit http://security.ubuntu.com precise-security/main i386 Packages                          
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                    
Hit http://extras.ubuntu.com precise/main i386 Packages                                     
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Hit http://us.archive.ubuntu.com precise-updates Release             
Hit http://security.ubuntu.com precise-security/universe i386 Packages                      
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports Release           
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                                
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise/main i386 Packages          
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Reading package lists... Done
```

I wonder why the source repos are active on a default install. Were they set like that in 11.10?

---

### Post by Zill on 2012-05-12
> **vasa1 said:**
> @skew and @zill, would you mind looking at [http://askubuntu.com/questions/135818/ubuntu-update-cache-too-big](http://askubuntu.com/questions/135818/ubuntu-update-cache-too-big) and my comment there?
You seem to have identified a similar problem to the OP's.

FWIW, I have just run sudo apt-get update which downloaded 13.1MB.  I then *immediately* ran the same command again and *nothing* was downloaded.  Note that this does not include source code lists.

As I run 10.04 (Lucid) rather than 11.10 or 12.04, it does look like this is a bug that has been introduced in later releases.

I can only suggest that those experiencing this problem raise a bug report.

---

### Post by vasa1 on 2012-05-12
> **Zill said:**
> You seem to have identified a similar problem to the OP's.

FWIW, I have just run sudo apt-get update which downloaded 13.1MB.  I then *immediately* ran the same command again and *nothing* was downloaded.  Note that this does not include source code lists.
...
With which Ubuntu version was that?

In my case, I just ran the command and got
```
Fetched 6,518 kB in 3min 44s (29.0 kB/s)
```
I then ran it immediately again and got
```
Fetched 6,227 kB in 3min 38s (28.5 kB/s)
```Spooky :(
In both cases, the next lines were```
Reading package lists... Done
Working...
No files to download.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by vasa1 on 2012-05-12
> **CharlesA said:**
> Sounds about right. 

I just did an apt-get update on my server (which has all the deb-src lines commented out) and it didn't need to download anything.

However, on my Precise desktop install with an unmodified sources.list file, I kept having to download 19 megs or so each time I ran an apt-get update:

```
...
```

After commenting out the deb-src lines, I didn't download anything.
```
...
```

I wonder why the source repos are active on a default install. Were they set like that in 11.10?

I did a clean install of 12.04 **RC** and then just kept updating it. I thought that maybe that was why I had the source repos enabled. Anyway, I've had them disabled for several days and several updates but still see the ~6 MB downloads (no source repos) each time I run sudo apt-get update even when I run the same command immediately after the first concludes.

---

### Post by hottarod on 2012-05-12
Update manager quit notifying me of updates after I upgraded 12.04.  I just checked and I have 125 megabytes of downloading to do this morning.

---

### Post by CharlesA on 2012-05-12
> **vasa1 said:**
> I did a clean install of 12.04 **RC** and then just kept updating it. I thought that maybe that was why I had the source repos enabled. Anyway, I've had them disabled for several days and several updates but still see the ~6 MB downloads (no source repos) each time I run sudo apt-get update even when I run the same command immediately after the first concludes.
Mine is a clean install of 12.04. The source repos seem to be enabled by default for some reason.

I wonder why you keep having to download an update index.

---

### Post by EzioAuditore on 2012-05-12
> **skew said:**
> For us poor slobs who STILL have no choice but to use dial-up, due to where we live. The 15-22mb download required to refresh the update list everyday is untenable, at best.

   This appears to be a recent phenomena. Is there something new going on with the update system (bug, software change, etc)? I did'nt have this problem until about a month or so ago. From what I've read on another forum (thats now closed) I'm not the only person who's experiencing this.

[http://ubuntuforums.org/showthread.php?t=1964421&highlight=apt-get+download+all+list+everyday+lists+huge](http://ubuntuforums.org/showthread.php?t=1964421&highlight=apt-get+download+all+list+everyday+lists+huge)

  Is their any other options available to keep on top of security updates without this drawn out daily download? Currently it can take an hour to an hour and a half to download the lists. I've used both the CL 'apt-get update' and the Update-Manager with the same results. From what I can see the lists are usually the same in size and content from the lists download from the day before. the only change which I can find being that the /var/lib/apt/periodic/update-success-stamp  date has changed.  

Any thoughts? 

Thanks!

Hey mate your not alone in that.. Me too getting the same behavior. Source packages are commented out but still no good. And stuck with a 2G network so its same as dial-up.

```
sudo apt-get update
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Ign http://in.archive.ubuntu.com precise InRelease                             
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://in.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:4 http://dl.google.com stable Release [1,347 B]                            
Get:5 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:7 http://dl.google.com stable/main amd64 Packages [1,245 B]                
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Get:8 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://ppa.launchpad.net precise Release                                   
Get:9 http://dl.google.com stable/main i386 Packages [1,268 B]                 
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:10 http://in.archive.ubuntu.com precise Release [49.6 kB]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:11 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]          
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [32.9 kB]
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://archive.canonical.com precise/partner Translation-en_IN             
Ign http://dl.google.com stable/main Translation-en                            
Get:14 http://in.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:15 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:16 http://security.ubuntu.com precise-security/universe amd64 Packages [8,581 B]
Get:17 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,142 B]
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [32.9 kB]
Get:19 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:20 http://security.ubuntu.com precise-security/universe i386 Packages [8,594 B]
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://ppa.launchpad.net precise/main Translation-en_IN                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_IN                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_IN                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:22 http://in.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:23 http://in.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:24 http://in.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:25 http://in.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:26 http://in.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:27 http://in.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:28 http://in.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex             
Get:29 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [95.2 kB]
Get:30 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [757 B]
Get:31 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [27.5 kB]
Get:32 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,142 B]
Get:33 http://in.archive.ubuntu.com precise-updates/main i386 Packages [96.5 kB]
Get:34 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]
Get:35 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [27.7 kB]
Get:36 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:37 http://in.archive.ubuntu.com precise-backports/main amd64 Packages [559 B]
Get:38 http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:39 http://in.archive.ubuntu.com precise-backports/universe amd64 Packages [1,387 B]
Get:40 http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]
Get:41 http://in.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:42 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:43 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [1,391 B]
Get:44 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 12.9 MB in 19min 51s (10.8 kB/s)
Reading package lists... Done

```

---

### Post by Zill on 2012-05-12
> **vasa1 said:**
> With which Ubuntu version was that?...
> **Zill said:**
> ...**[COLOR="Red"]As I run 10.04 (Lucid)[/COLOR]** rather than 11.10 or 12.04, it does look like this is a bug that has been introduced in later releases...[COLOR="White"].[/COLOR]

---

### Post by vasa1 on 2012-05-12
> **Zill said:**
> [COLOR="White"].[/COLOR]

But why did you get a ~13 MB update then? Isn't that odd?

---

### Post by Zill on 2012-05-12
> **vasa1 said:**
> But why did you get a ~13 MB update then? Isn't that odd?
This was my first update today.  Subsequent updates today had zero downloads.

---

### Post by HugoNotte on 2012-05-13
I have got the same problem with Mint 11, Mint 12, Ubuntu 11.10 & 12.04

Several weeks ago, the refresh of the update manger started blocking our slow ADSL line or eating MB on the faster mobile connection, which is expensive. Until then, I have not had the problem, neither on Ubuntu 11.10 nor Mint 11.
When looking at the lists, the main culprit seems to be some Ubuntu I386 repsotory, which downloads 15-18 MB each refresh. Disabling automatic refresh in the update manager doesn't seem to help, all computers of mine still feel the urge to download close to 30 MB for nothing at least once a day.

I have since started using OpenSuse 12.1 and there is no such thing happening. It's a great saver on bandwidth or dataplan. It takes a bit of getting used to, but in the end OpenSuse works just as well as Ubuntu does. If Canonical feels it's ok to waist our bandwidth, there are other distros out there.

---

### Post by coldraven on 2012-05-13
I just read this but I have not tried it, it claims to speed up your updates.
Has anybody used it?
[http://www.ubuntubuzz.com/2012/05/prozilla-and-apt-proz-now-can-be.html#more](http://www.ubuntubuzz.com/2012/05/prozilla-and-apt-proz-now-can-be.html#more)

---

### Post by skew on 2012-05-24
This is still a major problem for me.  If it's not fixed soon I'll have no choice but to jump ship to another distro. Damn pity.

Here are the related bug reports.

[https://bugs.launchpad.net/launchpad/+bug/1001780](https://bugs.launchpad.net/launchpad/+bug/1001780)

[https://bugs.launchpad.net/launchpad/+bug/1001886](https://bugs.launchpad.net/launchpad/+bug/1001886)

---

### Post by skew on 2012-06-07
I finally gave up! I've moved to another distro and am now much happier. 

The problem it appears, from what I've read, is restricted only to Ubuntu repositories. Since they (ubuntu) don't appear to be doing anything to fix it I can only assume that they don't intend to.

I've been with Ubuuntu since Dapper and loved it. However that warm glow faded over the years. Among the problems were; creeping regression, Unity  and now this. 

As such it's time to move to a better product. Which I'll attest do indeed exist out there.

---

### Post by Zill on 2012-06-07
> **skew said:**
> I finally gave up! I've moved to another distro and am now much happier...
Well, I am sorry to see you move on but I can understand why.  Personally, I am still running 10.04 LTS, and have broadband, so haven't really been affected by this problem.  However, I do agree this does seem to be an unacceptable bug.  As [bug #1001780]("https://bugs.launchpad.net/launchpad/+bug/1001780") has now been confirmed, hopefully work will now be done to resolve the problem.

> **skew said:**
> ...I've been with Ubuuntu since Dapper and loved it. However that warm glow faded over the years. Among the problems were; creeping regression, Unity  and now this...
Again, having been using Ubuntu myself since Breezy Badger, I have to agree with your comments.  IMHO Ubuntu does seem to be being "dumbed-down" with more emphasis on glitzy graphics rather than making it the fast, lean, functional and reliable OS it could be.

As you have established, there are other Linux OS's out there that may be better suited to your requirements.  Although not my primary OS (yet!), I do use [CrunchBang Linux]("http://crunchbanglinux.org/").  Although not suited to less-experienced users IMO, this does meet a lot of my requirements in a way that the later Ubuntu releases do not.

Out of interest, would you mind telling us which distro you have moved to?

---

### Post by forrestcupp on 2012-06-07
One thing people could do until this is fixed is to change the settings in Update Manager. Change the "Automatically check for updates" box to "Weekly", "Every two weeks", or even "Never". If you set it to never automatically check for updates, then you'll only have to suffer through waiting when you choose to do it manually. If you have a slow connection and it's a hindrance for you, there's no reason to have it set to do that every day.

I will say that unchecking the Source box helped me out a lot.

---

