---
title: "Updates not downloading (Firefox-related?)"
date: 2012-01-08
forum: General Help
---

### Post by Ertai87 on 2012-01-08
I have an icon in the top corner of my screen telling me something about non-updated repositories.  When I go to update, it says it's unable to update ppa:mozillateam/firefox-stable because there's a 404 error.  I tried removing that ppa from my sources (using add-apt-repository -r) but it didn't solve it.  How do I:

1) Get rid of this warning?
2) Add a working Firefox repository so that I can continue to get updates for Firefox?

Thanks.

---

### Post by bluexrider on 2012-01-08
if you have been receiving updates to this point it may be the PPA itself that has the problem. 

you could edit the source file and eliminate the offending PPA then add one. 

please post results of this

```
sudo apt-get update 
```

---

### Post by Ertai87 on 2012-01-08
```
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ftp.jaist.ac.jp oneiric InRelease                                   
Ign http://ftp.jaist.ac.jp oneiric-updates InRelease                 
Ign http://ftp.jaist.ac.jp oneiric-security InRelease                
Get:1 http://dl.google.com stable Release.gpg [198 B]                
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://ftp.jaist.ac.jp oneiric Release.gpg                                 
Hit http://archive.canonical.com oneiric Release                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Get:3 http://dl.google.com stable/main i386 Packages [1,203 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Hit http://ftp.jaist.ac.jp oneiric-updates Release.gpg
Ign http://archive.canonical.com oneiric/partner TranslationIndex    
Err http://ppa.launchpad.net oneiric/main Sources                    
  
Err http://ppa.launchpad.net oneiric/main Sources
  
Hit http://ftp.jaist.ac.jp oneiric-security Release.gpg
Err http://ppa.launchpad.net oneiric/main Sources                    
  
Hit http://ftp.jaist.ac.jp oneiric Release                           
Err http://ppa.launchpad.net oneiric/main Sources                              
  
Err http://ppa.launchpad.net oneiric/main Sources                    
  404  Not Found
Hit http://ftp.jaist.ac.jp oneiric-updates Release
Hit http://ftp.jaist.ac.jp oneiric-security Release                   
Hit http://ftp.jaist.ac.jp oneiric/main Sources                       
Hit http://ftp.jaist.ac.jp oneiric/restricted Sources
Hit http://ftp.jaist.ac.jp oneiric/universe Sources
Hit http://ftp.jaist.ac.jp oneiric/multiverse Sources
Hit http://ftp.jaist.ac.jp oneiric/main i386 Packages
Hit http://ftp.jaist.ac.jp oneiric/restricted i386 Packages
Hit http://ftp.jaist.ac.jp oneiric/universe i386 Packages
Hit http://ftp.jaist.ac.jp oneiric/multiverse i386 Packages
Hit http://ftp.jaist.ac.jp oneiric/main TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric/multiverse TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric/restricted TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric/universe TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-updates/main Sources
Hit http://ftp.jaist.ac.jp oneiric-updates/restricted Sources
Hit http://ftp.jaist.ac.jp oneiric-updates/universe Sources
Ign http://dl.google.com stable/main Translation-en_US
Hit http://ftp.jaist.ac.jp oneiric-updates/multiverse Sources
Hit http://ftp.jaist.ac.jp oneiric-updates/main i386 Packages        
Hit http://ftp.jaist.ac.jp oneiric-updates/restricted i386 Packages  
Hit http://ftp.jaist.ac.jp oneiric-updates/universe i386 Packages    
Ign http://dl.google.com stable/main Translation-en                  
Hit http://ftp.jaist.ac.jp oneiric-updates/multiverse i386 Packages  
Hit http://ftp.jaist.ac.jp oneiric-updates/main TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-updates/multiverse TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-updates/restricted TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-updates/universe TranslationIndex
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Hit http://ftp.jaist.ac.jp oneiric-security/main Sources
Ign http://archive.canonical.com oneiric/partner Translation-en
Hit http://ftp.jaist.ac.jp oneiric-security/restricted Sources
Hit http://ftp.jaist.ac.jp oneiric-security/universe Sources
Hit http://ftp.jaist.ac.jp oneiric-security/multiverse Sources
Hit http://ftp.jaist.ac.jp oneiric-security/main i386 Packages
Hit http://ftp.jaist.ac.jp oneiric-security/restricted i386 Packages
Hit http://ftp.jaist.ac.jp oneiric-security/universe i386 Packages
Hit http://ftp.jaist.ac.jp oneiric-security/multiverse i386 Packages
Hit http://ftp.jaist.ac.jp oneiric-security/main TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-security/multiverse TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-security/restricted TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric-security/universe TranslationIndex
Hit http://ftp.jaist.ac.jp oneiric/main Translation-en
Hit http://ftp.jaist.ac.jp oneiric/multiverse Translation-en
Hit http://ftp.jaist.ac.jp oneiric/restricted Translation-en
Hit http://ftp.jaist.ac.jp oneiric/universe Translation-en
Hit http://ftp.jaist.ac.jp oneiric-updates/main Translation-en
Hit http://ftp.jaist.ac.jp oneiric-updates/multiverse Translation-en
Hit http://ftp.jaist.ac.jp oneiric-updates/restricted Translation-en
Hit http://ftp.jaist.ac.jp oneiric-updates/universe Translation-en
Hit http://ftp.jaist.ac.jp oneiric-security/main Translation-en
Hit http://ftp.jaist.ac.jp oneiric-security/multiverse Translation-en          
Hit http://ftp.jaist.ac.jp oneiric-security/restricted Translation-en          
Hit http://ftp.jaist.ac.jp oneiric-security/universe Translation-en            
Fetched 2,748 B in 6s (444 B/s)                                                
W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by bluexrider on 2012-01-08
need to edit the sources.list file

Make a backup of the file
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```Now to edit the file
```
sudo gedit /etc/apt/sources.list
```scroll to 
[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)

add "#" at the beginning of the line so it looks like this:

#[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)
save and close

Update
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Ertai87 on 2012-01-08
There is no such line:

[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)

I did CTRL-F for "firefox" and got no hits.

---

### Post by bluexrider on 2012-01-08
> **Ertai87 said:**
> There is no such line:

[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)

I did CTRL-F for "firefox" and got no hits.


Your system has a PPA that doesn't exist.
  There is no Firefox-stable PPA for Oneric, as the latest Firefox is  already in the main repos. You will need to remove this PPA from your  Software Sources.




Go to System->Administration and you should see 'Software Sources' in the menu.



[IMG]http://i.stack.imgur.com/arPRq.png[/IMG]
  You should see all of the repositories that you have added (including  the PPAs added via add-apt-repository). You can temporarily disable a  repository by unchecking the box next to it. To remove a repository  permanently, highlight it and click on the 'Remove' button. When you are  done, hit the 'Close' button.




Hope this helps

---

### Post by bluexrider on 2012-01-08
> **minins said:**
> you could edit the source file and eliminate the offending PPA then add one. 
There is no Firefox-stable PPA for Oneric, as the latest Firefox is  already in the main repos

---

### Post by Ertai87 on 2012-01-09
> **bluexrider said:**
> Your system has a PPA that doesn't exist.
  There is no Firefox-stable PPA for Oneric, as the latest Firefox is  already in the main repos. You will need to remove this PPA from your  Software Sources.




Go to System->Administration and you should see 'Software Sources' in the menu.



[IMG]http://i.stack.imgur.com/arPRq.png[/IMG]
  You should see all of the repositories that you have added (including  the PPAs added via add-apt-repository). You can temporarily disable a  repository by unchecking the box next to it. To remove a repository  permanently, highlight it and click on the 'Remove' button. When you are  done, hit the 'Close' button.




Hope this helps

Alright, that solved it, thanks!

---

### Post by RomaSonic777 on 2012-03-19
Hey i tought i just metion this. I had some problems with instaling updates on a new ubuntu install on a win7 PC. I already had ubuntu on another PC and all updates were downloading fine. What i saw is that the download location for the updates were different on the new PC. I canged this location to USA and all updates were downloading fine after that. The download location can be changed under system settings and software sources. Hope this helps.

---

