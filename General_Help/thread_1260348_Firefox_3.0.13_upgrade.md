---
title: "Firefox 3.0.13 upgrade"
date: 2009-09-07
forum: General Help
---

### Post by motorcity909 on 2009-09-07
Hi all, Update Manager brings up an upgrade to Firefox every day (see screengrab).  

I use Ubuntuzilla and so have already upgraded to the latest version - Firefox 3.5.2.  

If I install the 3.0.13 update, will that over-write 3.5.2?  

If so, I won't want to install 3.0.13 so how can I stop those updates showing in Update Manager?

Thanks as always.

---

### Post by ajgreeny on 2009-09-07
Updating firefox to 3.0.13 will not affect firefox 3.5, as that is installed as well as 3.0.13, if you did it with the repos version, but I'm not sure about the version downloaded from mozilla, though I think it is the same situation.
To pin a package version and stop it appearing in both Synaptic and Update Manager and also if you **sudo apt-get upgrade** add these lines to  /etc/apt/preferences:

```
Package: firefox                
Pin: version 3.0.12           (or whatever version you have now)   
Pin-Priority: 1001
```    

I'm not sure if you will need to do it for the dependencies as well, or if stopping the main FF will also stop them, so give it a try first, and add them as well if needed

---

### Post by linuxwizard on 2009-09-07
It is safe to update your 3.0.13 Firefox.

 Firefox] Older version showing up in Synaptic and Update Manager. What do I do?

This is expected behavior: Ubuntuzilla installs the latest release in parallel to the repositories version, so they coexist side by side without interference. Go ahead and carry out the upgrade when one is offered, your default software is still going to be the latest official Mozilla build, as installed by Ubuntuzilla. 

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ)

[http://ubuntuforums.org/showthread.php?t=1221630](http://ubuntuforums.org/showthread.php?t=1221630)

---

### Post by motorcity909 on 2009-09-08
Thanks everyone.  I ran the update tonight and FF 3.5.2 is unaffected.

Cheers all.

---

