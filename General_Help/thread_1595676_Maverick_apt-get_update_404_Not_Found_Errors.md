---
title: "Maverick apt-get update: 404 Not Found Errors"
date: 2010-10-13
forum: General Help
---

### Post by FaizanKazi on 2010-10-13
Hi all,
I'm getting a whole bunch of 404 Not found errors when using sudo apt-get update on ubuntu 10.10

Seems to be missing out on big sources, like the Gnome-Do repository and
[http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources

Please check the output below for details:


faizan@faizan-laptop:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/gnurubuntu/rubuntu/ubuntu/](http://ppa.launchpad.net/gnurubuntu/rubuntu/ubuntu/) lucid/main Translation-en
Ign [http://ppa.launchpad.net/gnurubuntu/rubuntu/ubuntu/](http://ppa.launchpad.net/gnurubuntu/rubuntu/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/do-core/ppa/ubuntu/](http://ppa.launchpad.net/do-core/ppa/ubuntu/) maverick/main Translation-en  
Ign [http://ppa.launchpad.net/do-core/ppa/ubuntu/](http://ppa.launchpad.net/do-core/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ricotz/testing/ubuntu/](http://ppa.launchpad.net/ricotz/testing/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ricotz/testing/ubuntu/](http://ppa.launchpad.net/ricotz/testing/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Hit [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release.gpg                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) maverick/non-free Translation-en
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) maverick/non-free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en 
Hit [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://download.virtualbox.org](http://download.virtualbox.org) maverick/non-free i386 Packages             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages [3,086B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Fetched 60.7kB in 3s (18.3kB/s)
W: Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by marshmallow1304 on 2010-10-13
It looks like do-core has not made a Maverick branch for their PPA.  Or a Lucid branch for that matter.  They haven't updated that PPA for 36 weeks.  To get around this, you can replace maverick with karmic for those two sources.

---

### Post by FaizanKazi on 2010-10-14
Oh ok! I didnt realize... I wonder why... :s I'll replace it with Karmic then :) thanks for your help!

> **marshmallow1304 said:**
> It looks like do-core has not made a Maverick branch for their PPA.  Or a Lucid branch for that matter.  They haven't updated that PPA for 36 weeks.  To get around this, you can replace maverick with karmic for those two sources.

---

### Post by preahkumpii on 2010-10-23
I am having the same problem, except that I am updating via the Update Manager. Can you please provide the solution a little less techie way. I lost you when trying to understand how to fix it. Also, what causes the problem? I was hoping not for a workaround that I will have to undo later, but a real solution. Again, I don't fully understand the problem in the first place. Thanks.

Adam

---

### Post by sinisterstuf on 2011-05-16
> **preahkumpii said:**
> I am having the same problem, except that I am updating via the Update Manager. Can you please provide the solution a little less techie way. I lost you when trying to understand how to fix it. Also, what causes the problem? I was hoping not for a workaround that I will have to undo later, but a real solution. Again, I don't fully understand the problem in the first place. Thanks.

Adam

[LIST=1]
[*]**Take note of which PPA/source is giving you a problem** (write it down or something)

[*]**Start the _Synaptic Package Manager_**
[LIST][*]System > Administration > Synaptic[/LIST]

[*]**Edit your _Software Sources_**
[LIST]
[*]Settings > Repositories (in package manager)
[*]Go to the tab that says 'Other Software'
[*]Go Select the PPA/source you wrote down earlier and click [Edit…]
[*]If you're sure the URI is correct, change the text in the 'Distribution' field from *maverick* to *karmic* or whatever distribution is available for that repository.
[*]You might want to do the same for the 'source' repository as well.
[*]Click [Close]
[/LIST]

[*]**Refresh your package list**
[LIST]
[*]You should get a message telling you to do this.
[*]Select: Edit > Reload Package Information
[*]That should update your repositories and fix your problem.
[/LIST]
[/LIST]

You should now be able to close synaptic and run _Update Manager_ successfully. :D (I didn't check but there might be an option to access the _Software Sources_ from the _Update Manager_).
**Did this answer your question?**

---

