---
title: "Update Manager: &quot;Check your internet connection.&quot;"
date: 2010-11-22
forum: General Help
---

### Post by Karandr on 2010-11-22
Hi there,
[INDENT]I'm running Maverick, and I just went to install some updates when I got [this]("http://imgur.com/c0Isp") error message. As you can see from the screenshot (and the fact that I'm posting this thread), I am connected (full bars, whoo), so I'm somewhat confused as to a) why this error message is appearing and b) what I can do to fix it. 

If anyone could help me with this, I'd greatly appreciate it.

Thanks for your time!
[/INDENT]

---

### Post by dcstar on 2010-11-22
> **Karandr said:**
> Hi there,
[INDENT]I'm running Maverick, and I just went to install some updates when I got [this]("http://imgur.com/c0Isp") error message. As you can see from the screenshot (and the fact that I'm posting this thread), I am connected (full bars, whoo), so I'm somewhat confused as to a) why this error message is appearing and b) what I can do to fix it. 

If anyone could help me with this, I'd greatly appreciate it.

Thanks for your time!
[/INDENT]

What is in the **Details**???

---

### Post by Karandr on 2010-11-22
> **dcstar said:**
> What is in the **Details**???

[INDENT]Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-inspector_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_all.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-inspector_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_all.deb) 404  Not Found

Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_i386.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_i386.deb) 404  Not Found
[/INDENT]

---

### Post by psavva on 2010-11-22
> **Karandr said:**
> [INDENT]Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-inspector_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_all.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-inspector_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_all.deb) 404  Not Found

Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_i386.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_i386.deb) 404  Not Found
[/INDENT]

Update your sources to:
```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main 
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main 

```
Your sources file is: ```
/etc/apt/sources.list
```
Read This if yo are not sure how to change it :)
[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

---

### Post by Karandr on 2010-11-22
> **psavva said:**
> Update your sources to:
```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main 
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main 

```Your sources file is: ```
/etc/apt/sources.list
```Read This if yo are not sure how to change it :)
[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)


When I open up the Software Sources settings, those PPAs are the ones already in there. I thought I might need to have "deb" and "deb-src" before the url, but the "OK" button was greyed out as soon as I typed that, so I guess not.

I am le confused.

---

### Post by mc4man on 2010-11-22
try running this first 
sudo apt-get update 
As you could see here the package for maverick has been updated  - chromium-browser-inspector_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_all.deb 
is no longer available
now - .......r66904.....
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/)

---

### Post by Karandr on 2010-11-22
> **mc4man said:**
> try running this first 
sudo apt-get update 
As you could see here the package for maverick has been updated  - chromium-browser-inspector_9.0.591.0~svn20101120r66866-0ubuntu1~ucd1~maverick_all.deb 
is no longer available
now - .......r66904.....
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/)
Mmm, sudo apt-get fails somewhat miserably.

I'm not sure what exactly I'm supposed to do with the url you gave me.
I'm really sorry if I appear a bit dim -- I'm extremely tired.

---

### Post by mc4man on 2010-11-22
> sudo apt-get fails somewhat miserably
you may wish to post the terminal output that "... miserably"  - as in open a terminal and run this
```
sudo apt-get update
```
> I'm not sure what exactly I'm supposed to do with the url you gave me.

While you could actually use that page to dl and manually update, I gave it to you to show that the errors you posted were correct - they can't be found because the packages no longer exist 
> 
Originally Posted by Karandr 
    Failed to fetch [http://ppa.launchpad.net/chromium-da...verick_all.deb](http://ppa.launchpad.net/chromium-da...verick_all.deb) 404 Not Found

    Failed to fetch [http://ppa.launchpad.net/chromium-da...erick_i386.deb](http://ppa.launchpad.net/chromium-da...erick_i386.deb) 404 Not Found

---

### Post by Karandr on 2010-11-22
> **mc4man said:**
> you may wish to post the terminal output that "... miserably"  - as in open a terminal and run this
```
sudo apt-get update
```While you could actually use that page to dl and manually update, I gave it to you to show that the errors you posted were correct - they can't be found because the packages no longer exist
Hnng, I apologize profusely.

Might I add that I only assume it failed miserably because of the copious amounts on 404s towards the end.

```
Get:1 http://linux.dropbox.com maverick Release.gpg                            
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ maverick/partner Translation-en              
Get:2 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                 
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://archive.canonical.com/ maverick/partner Translation-en_US           
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://archive.canonical.com maverick Release                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Get:3 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Get:4 http://extras.ubuntu.com maverick Release [57.3kB]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Hit http://deb.opera.com stable Release                                        
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/ maverick/main Translation-en_US
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://linux.dropbox.com maverick Release                                  
Ign http://ppa.launchpad.net/cardapio-team/unstable/ubuntu/ maverick/main Translation-en
Err http://linux.dropbox.com maverick Release                                  
  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Ign http://deb.opera.com stable/non-free i386 Packages                         
Ign http://ppa.launchpad.net/cardapio-team/unstable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en
Hit http://security.ubuntu.com maverick-security/main Sources                  
Get:6 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]           
Ign http://deb.opera.com stable/non-free i386 Packages                         
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ilap/lwp/ubuntu/ maverick/main Translation-en     
Ign http://ppa.launchpad.net/ilap/lwp/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages    
Hit http://security.ubuntu.com maverick-security/universe i386 Packages      
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages    
Hit http://ppa.launchpad.net maverick Release.gpg                            
Ign http://ppa.launchpad.net/leolik/leolik/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/leolik/leolik/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                    
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://us.archive.ubuntu.com maverick/restricted Sources         
Hit http://us.archive.ubuntu.com maverick/universe Sources           
Hit http://us.archive.ubuntu.com maverick/multiverse Sources         
Hit http://us.archive.ubuntu.com maverick/main i386 Packages         
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages   
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/ maverick/main Translation-en_US
Get:7 http://ppa.launchpad.net maverick Release.gpg [316B]           
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release  
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages     
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages   
Get:8 http://us.archive.ubuntu.com maverick-updates/main Sources [39.8kB]
Ign http://ppa.launchpad.net maverick Release                               
Hit http://ppa.launchpad.net maverick Release                                
Hit http://ppa.launchpad.net maverick Release                                
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Get:9 http://ppa.launchpad.net maverick Release [39.8kB]                       
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                
Hit http://ppa.launchpad.net maverick Release                                
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Get:10 http://us.archive.ubuntu.com maverick-updates/restricted Sources [14B]  
Get:11 http://us.archive.ubuntu.com maverick-updates/universe Sources [12.6kB]
Get:12 http://us.archive.ubuntu.com maverick-updates/multiverse Sources [649B] 
Get:13 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [102kB]
Ign http://ppa.launchpad.net maverick Release                                  
Get:14 http://ppa.launchpad.net maverick Release [39.8kB]                    
Hit http://www.sourceslist.eu lucid Release.gpg                                
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Get:15 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:16 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [40.0kB]
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:17 http://ppa.launchpad.net maverick/main Sources [692B]                   
Get:18 http://ppa.launchpad.net maverick/main i386 Packages [625B]             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:19 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [1,958B]
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Get:20 http://ppa.launchpad.net maverick/main Sources [3,966B]                 
Get:21 http://ppa.launchpad.net maverick/main i386 Packages [10.4kB]           
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Ign http://www.sourceslist.eu/repo/ubuntu/ lucid/main Translation-en           
Ign http://www.sourceslist.eu/repo/ubuntu/ lucid/main Translation-en_US
Ign http://www.sourceslist.eu/repo/ubuntu/ lucid/nonon-free Translation-en
Ign http://www.sourceslist.eu/repo/ubuntu/ lucid/nonon-free Translation-en_US
Hit http://www.sourceslist.eu lucid Release          
Ign http://www.sourceslist.eu lucid/main i386 Packages
Ign http://www.sourceslist.eu lucid/main i386 Packages
Hit http://www.sourceslist.eu lucid/main i386 Packages
Fetched 325kB in 4min 34s (1,181B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://linux.dropbox.com maverick Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://www.sourceslist.eu/repo/ubuntu/dists/lucid/Release  Unable to find expected entry  nonon-free/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

..again, I am so, so, sorry for everything, including that giant wall of text and whatever elementary mistakes I may make in the future.

---

### Post by mc4man on 2010-11-22
Not sure where you stand atm but - your sources list is a mess. You should definatly clean it up. Any ppa you have enabled that is getting a 404 should be disabled or removed. Then find the ppa and if you still want it AND it has maverick packages add it, either as new or adjust your current url(s)

You also appear to have lucid repo's enabled - those should be removed.
So you may wish to go to Software Sources -> other and disable/remove any invalid ppa's.

If inclinded also post this (cat or gedit
```
gedit /etc/apt/sources.list
```
and 
```
ls /etc/apt/sources.list.d
```

---

### Post by Karandr on 2010-11-23
> **mc4man said:**
> Not sure where you stand atm but - your sources list is a mess. You should definatly clean it up. Any ppa you have enabled that is getting a 404 should be disabled or removed. Then find the ppa and if you still want it AND it has maverick packages add it, either as new or adjust your current url(s)

You also appear to have lucid repo's enabled - those should be removed.
So you may wish to go to Software Sources -> other and disable/remove any invalid ppa's.

If inclinded also post this (cat or gedit
```
gedit /etc/apt/sources.list
```and 
```
ls /etc/apt/sources.list.d
```
Interestingly enough, I just tried running Update Manager and everything seems to be running smoothly, so I'm bemused but pleased.

Per your advice, I've also cleaned up my sources list.

As everything is/seems to be working fine, should I still post the gedit and ls commands?

---

### Post by fallvine on 2011-03-30
still a newbie using lucid lynx, as i ran update manager, i get this message Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

how to fix this or should i simply ignore this

thanks in advance...

---

### Post by rickcjmac on 2011-04-09
Another thread solved this problem

> You can disable the PPA via menus System, Administration, Synaptic Package Manager, Settings, Repositories, Other Software tab.

[http://ubuntuforums.org/archive/index.php/t-1589372.html]("http://ubuntuforums.org/archive/index.php/t-1589372.html")

Hope this helps :)

---

