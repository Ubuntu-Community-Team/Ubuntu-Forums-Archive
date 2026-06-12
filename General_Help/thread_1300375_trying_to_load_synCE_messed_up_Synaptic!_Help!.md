---
title: "trying to load synCE messed up Synaptic! Help!"
date: 2009-10-24
forum: General Help
---

### Post by pstrbrc on 2009-10-24
OK, I'm trying to get my ipaq w/Win Mobile 5.0 to work, and I came across synCE. [http://www.synce.org/moin/FrontPage]("http://www.synce.org/moin/FrontPage")
Seemed like a good idea, so I followed their instructions on [their installation page]("http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice") but when I did this
> #

Go to System -> Administration -> Software Sources
# Click on Third Party software
# Click Add...
# Paste the line:

    *

      deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) your_ubuntu_version main
          o

            where you replace your_ubuntu_version with hardy, intrepid, or jaunty, depending on which version you are running. 

# Click Close
# Click Reload 

I got an error message, and now when I open up Synaptic, I get THIS error message:

> E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How do I fix this?

---

### Post by pstrbrc on 2009-10-24
OK, knuckle head me. Fixed the line 54 error, now trying to install synCE. So I'm stuck here:

> pstrbrc@pstrbrc-laptop:~$ sudo apt-get install synce-hal librra0-tools librapi2-tools
[sudo] password for pstrbrc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synce-hal is already the newest version.
synce-hal set to manually installed.
Package librra0-tools is a virtual package provided by:
  librra-tools 0.14-0ubuntu0~ppa1~jaunty1
You should explicitly select one to install.
E: Package librra0-tools has no installation candidate


I'm not smart enough to know exactly what that means. I'm assuming that it's telling me I have choices. What do I need to know?

---

### Post by pstrbrc on 2009-10-27
resolved.:D

---

