---
title: "Upgrading from 6.10 (Edgy) to latest"
date: 2010-09-02
forum: General Help
---

### Post by starbard on 2010-09-02
I'm currently running server version 6.10 and would like to upgrade to the current release (10.04).  Can someone point me toward the proper resources/documentation for accomplishing this?

Thanks in advance for any help.

Al

---

### Post by llamabr on 2010-09-02
For best results, you'd really want to upgrade one release at a time, and for you, that would take all night.

Can't you back up your important data, and just do a fresh install?  It'll take 20 minutes.

---

### Post by starbard on 2010-09-02
I could but I hate to lose my current configurations and have to reinstall other packages I already have installed.  I don't mind doing one release at a time if I can accomplish this.

Al

---

### Post by Smart Viking on 2010-09-02
```
sudo apt-get dist-upgrade
```

---

### Post by arpanaut on 2010-09-02
Here's some resources:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg02781.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg02781.html)

Good luck...

Have a good back-up!
Going through so many upgrades, I would think that there is a high likelihood of something going wrong
Be prepared to start fresh.

---

### Post by starbard on 2010-09-02
I did an apt-get update and got a lot of the 404s.  Here's some of the output:

sudo apt-get update
Ign [http://debian.slimdevices.com](http://debian.slimdevices.com) stable Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                             
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                                  
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                            
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                                   
  404 Not Found [IP: 91.189.88.37 80]
Get:1 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release.gpg                                                 
Ign [http://debian.slimdevices.com](http://debian.slimdevices.com) stable/main Translation-en_US                             
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                             
  404 Not Found [IP: 91.189.88.37 80]
.
.
.


Then it ends with the following:

Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Should I be concerned about these errors? Will this cause problems if I do a dist-upgrade as suggested?

Thanks,
Al

---

### Post by valbaca on 2010-09-02
Since Edgy isn't supported anymore (and hasn't for some time) it's unlikely you'll be able to upgrade without a clean install.

From [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

Users of Ubuntu 9.10 and Ubuntu 8.04 LTS can upgrade to Ubuntu 10.04 by a  convenient automated process. Users of other Ubuntu releases need to  upgrade first to either Ubuntu 8.04 LTS or Ubuntu 9.10, and then to  10.04. Complete instructions may be found at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).

---

### Post by arpanaut on 2010-09-02
Yes those repositories no longer exist.

another link:  [http://www.rrfx.net/2009/07/upgrading-ubuntu-server-from-version.html](http://www.rrfx.net/2009/07/upgrading-ubuntu-server-from-version.html)

Once you get to a supported version or LTS it is easier, but with the change to Grub2 and the amount of changes in the past 3 or so years quite honestly you would be better off backing up, reinstalling, and going forward.

Next time try to stay more up to date,

P.S. If you truly have the server edition installed (not the Desktop version configured as a server) then the upgrade path might be different.
As the true "Server Edition" does have 5 yrs. support... bu your repos are looking for edgy and that is not a LTS so I don't know.

---

### Post by starbard on 2010-09-04
It is truly server edition but, as noted, it's not an LTS version.

I was afraid this wouldn't be easy but I thought I'd research it anyway.

Thanks for everyone's help.

Al

---

### Post by slakkie on 2010-09-07
> **starbard said:**
> It is truly server edition but, as noted, it's not an LTS version.

I was afraid this wouldn't be easy but I thought I'd research it anyway.

Thanks for everyone's help.

Al

[https://help.ubuntu.com/community/EOLUpgrades/Edgy](https://help.ubuntu.com/community/EOLUpgrades/Edgy)

That is the HOWTO you want to follow :)

---

