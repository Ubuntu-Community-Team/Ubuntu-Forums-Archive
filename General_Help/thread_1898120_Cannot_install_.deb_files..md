---
title: "Cannot install .deb files."
date: 2011-12-20
forum: General Help
---

### Post by Maleificus on 2011-12-20
Anytime I try to install a .deb file my package manager tells me that it failed to download the following packages, and I click on details and I get this: 
Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources 404 Not Found Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages 404 Not Found Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 404 Not Found Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources 404 Not Found Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages 404 Not Found Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages 404 Not Found 

Please help?

---

### Post by dabl on 2011-12-20
The problem is a network connectivity problem -- the APT system is not seeing the repositories.  It may be that they are temporarily offline, or it may be there is some intermediate problem between your location and the repos.

First recommendation is to wait an hour and try again.  Meanwhile, make sure other internet sites are not having the same problem.

---

### Post by t0p on 2011-12-20
I echo the previous comment.  Assuming you're not using the linux computer in question to post this: use the Ubuntu machine to see if you can access websites (eg google.com).  If you *can* browse the web, then the repository servers in question are offline at the moment.  Try again later.

---

### Post by Maleificus on 2011-12-20
Well, I am talking to you on my Kubuntu Distro right now, I do not have connectivity problems at all right now, I have been trying to get this to work for three days now before asking for help so I have already tried the wait an hour and try again.

---

### Post by dabl on 2011-12-20
OK I just checked my Kubuntu sources and I don't see the same Launchpad source repo that you are showing.  Are you sure it is correct?  I have these:

```
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu oneiric main

deb http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu oneiric main
```

---

### Post by Maleificus on 2011-12-20
I simply copy/pasted the output that I am getting, so yes I am sure it is correct. Is there a way to remove these repositories so it doesn't keep trying to download from them?

---

### Post by dabl on 2011-12-20
Use your editor in super-user mode, and edit them to match the ones I posted.

Alt-F2 "kdesudo kate" with no quote marks, then open each file and edit to match what you see above.  The files are in 

/etc/apt/sources.list.d/

After editing and saving, exit kate, then run in a terminal

sudo apt-get update

and see if it runs to completion.  If yes, you are good to go.

---

### Post by Maleificus on 2011-12-20
Okay, I did what you said and edited all the files in said folder, most of the 404s are gone except for two, these two still remain:

Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages
404  Not Found

Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
404  Not Found

---

### Post by dabl on 2011-12-20
Those are obviously bogus PPA addresses, at this point.  You need to figure out which files under /etc/apt/sources.list.d have that content, then you can either "sudo mv" or "sudo rm" them, in a terminal.

And again you will have to 

```
sudo apt-get update
```

to confirm that it's fixed.

---

### Post by dabl on 2011-12-20
If you can't find those repos under /etc/apt/sources.list.d/ then possibly they are under /etc/apt/

I hope they've not been inserted in /etc/apt/sources.list.  If they are, then you need to open that one for editing, and insert a "#" at the front of the bogus PPAs.

---

### Post by Maleificus on 2011-12-20
Sorry, I did not read that last post, let me check

---

### Post by Maleificus on 2011-12-20
Yeah I am not finding it in sources.list either, I did a control F search and found nothing. If he helps, here is the output from sudo apt-get update.



richard@Kelsie:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages/DiffIndex                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 316 B in 2s (117 B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

---

### Post by dabl on 2011-12-20
No, unfortunately that does not show the file location.  If, in a terminal, you will navigate to /etc/apt/sources.list.d/, I would like to see the output of 

```
ls
```

Have you installed muon?  If not, 

sudo apt-get update && sudo apt-get install muon.  Then we can use muon and maybe see something about the sources there.

---

### Post by Maleificus on 2011-12-20
I do have Muon installed, in fact I went into Muon while I was waiting for your response and I disabled all PPA's under Other Software, I then one by one enabled each of the PPAs until the error was recreated. I noticed that there are several PPAs that are [http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-ppa/ppa/ubuntu) and if I leave any one of those enabled the error gets re-created. However, if I leave them disabled I don't have the error.

---

### Post by dabl on 2011-12-20
OK, good.  If memory serves, those PPAs were used during the 11.10 development cycle, but then were obsoleted after it was released.  Whatever.  Just leave them disabled -- they obviously are not helping you.

---

### Post by dabl on 2011-12-20
Here's another good site to get Kubuntu help:  [http://www.kubuntuforums.net/index.php](http://www.kubuntuforums.net/index.php)

---

### Post by Maleificus on 2011-12-20
Awesome, well thank you for all of your help!

---

