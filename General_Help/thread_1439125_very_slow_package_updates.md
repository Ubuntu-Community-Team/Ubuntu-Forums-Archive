---
title: "very slow package updates"
date: 2010-03-25
forum: General Help
---

### Post by ScottishGirl on 2010-03-25
Hi everyone :)

For the last few weeks every time I run the following command *sudo apt-get update* it takes around 2 minutes to download even the smallest update list.  Below is a typical example:

Fetched 148kB in 2min 0s (1,225B/s)                                             
Reading package lists... Done        


My internet connection is working at normal speed, has anyone else had this annoying niggle?

---

### Post by ProfessionalOPs on 2010-03-25
this is happening to me now also.....i suspect it being heavy traffic.......when u run sudo apt-get update

does all of your Translation-en_US say ign in front of them
???

---

### Post by ScottishGirl on 2010-03-25
I should just mention that running *sudo apt-get upgrade* any package upgrades available are downloaded quickly.  I have Ubuntu 9.10 installed.

---

### Post by ProfessionalOPs on 2010-03-25
does ur sudo apt-get update hang at the [Waiting for header]??

---

### Post by ScottishGirl on 2010-03-25
> **ProfessionalOPs said:**
> does ur sudo apt-get update hang at the [Waiting for header]??

Yes!! :o

---

### Post by ScottishGirl on 2010-03-25
This is what I get after running the update command:

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_GB                
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages           
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Get: 3 [http://dl.google.com](http://dl.google.com) stable/main Packages [906B]
Fetched 3,635B in 2min 0s (30B/s)
Reading package lists... Done

---

### Post by imblack on 2010-03-25
This might be due to a slow mirror.
You can select the best possible mirror for your connection by running Software Sources from System->Administration, 
there you should find Download From: ______ Chose other from that list and click on select best possible server.

That worked for me, tell me if you still have problem.

Good day to you!

---

### Post by wojox on 2010-03-25
Do you have Google chrome/chromium installed? That's where it's hanging.

---

### Post by imblack on 2010-03-25
> **wojox said:**
> Do you have Google chrome/chromium installed? That's where it's hanging.
Can you please explain what Chrome has to do with slow apt-get update?

---

### Post by tgalati4 on 2010-03-25
Do you live near any large universities?  It's March Madness in the USA and that can slow down the tubez.

---

### Post by wojox on 2010-03-26
> **imblack said:**
> Can you please explain what Chrome has to do with slow apt-get update?

Because I had the same problem. Ditching Google's browser will speed it back up.

---

### Post by imblack on 2010-03-26
Dude either I'm psyched or you are making no sense.
What a browser has to do with getting packages from ubuntu archives?

---

### Post by wojox on 2010-03-26
```
Get: 2 http://dl.google.com  stable Release [2,540B]
Get: 3 http://dl.google.com stable/main Packages [906B]
```

That's Google's ppa for their browser which is what is causing the slow down which is in /etc/apt/sources.list.d

---

### Post by imblack on 2010-03-26
Ahhhh my bad, How can I be so dumb? I heard they are controlling our brains through micro waves :P
Got it now, if you have chrome you add the repositories in for them and they slow the update. Thanks mates for bearing up

---

### Post by wojox on 2010-03-26
My pleasure. :D

---

### Post by ubername on 2010-03-26
See this:
**apt-get update very slow after 99%**
[http://ubuntuforums.org/showthread.php?t=1437075](http://ubuntuforums.org/showthread.php?t=1437075)

and this:
**Google chrome (dev) sources.list problem**
[http://ubuntuforums.org/showthread.php?t=1430453](http://ubuntuforums.org/showthread.php?t=1430453)

---

### Post by wojox on 2010-03-26
Cool thanks ubername. :popcorn:

---

### Post by ScottishGirl on 2010-03-26
Hi guys

Removing Chrome - I never really used it- and un-ticking the Google box in Software Sources has made all the difference.  

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_GB            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages  
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                          
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources
Hit [http://deb.opera.com](http://deb.opera.com) stable Release        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Reading package lists... Done

Thanks for your advice.  :)

---

### Post by imblack on 2010-03-27
Another satisfied ubuntuer guys :)
Good work!

---

### Post by krige on 2010-04-09
I had the same problem but I liked Chrome too much to remove it.

I have fixed it by creating the file "/etc/apt/apt.conf.d/90localsettings" with the following content:

```
Acquire::http::Pipeline-Depth "0";
```

It seems Google recognizes this as a problem, but "there is no timeframe yet" for fixing it:
[http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3](http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3)

---

### Post by dcstar on 2010-11-07
> **krige said:**
> 
I have fixed it by creating the file "/etc/apt/apt.conf.d/90localsettings" with the following content:

```
Acquire::http::Pipeline-Depth "0";
```


That just fixed a very annoying problem with my 10.10 VMs - they were waiting for non-existent _AU repository files and the timeout wait was teeth-grinding.

Made this change and now all things happen instantly - thanks.

---

