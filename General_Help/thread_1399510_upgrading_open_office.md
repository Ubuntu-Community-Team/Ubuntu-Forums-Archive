---
title: "upgrading open office"
date: 2010-02-05
forum: General Help
---

### Post by windowsfree on 2010-02-05
I performed this once before on a different computer and it worked flawlessly, now on this machine, same OS as the other, I cannot get the upgrade to work.  These are the steps I used.


[LIST]
[*]Goto Terminal an copy-paste the following.
[/LIST]
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF**Adding  Repository**
 
[LIST]
[*]You will have to add the following new repo. Goto System->  Administration -> Software Sources, select the Thrid-Party Software  tab and Click ADD.
[/LIST]
 **For Ubuntu Jaunty**
 deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

**Upgrading to OpenOffice 3.1 in Ubuntu**
 
[LIST]
[*]Do the following in Terminal Window.
[/LIST]
                 sudo apt-get update
                sudo apt-get upgrade  



It did not upgrade.......


Any   suggestions ?

---

### Post by howefield on 2010-02-06
Not sure if this is the answer, is it this page your info came from ?

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)


If so, the PPA description says...

```
PPA description
Empty for now, will likely have OOo 3.2.0/3.2.1 debs for Karmic/Lucid later in the cycle.
If you want OOo 3.1.1 upgrade to Ubuntu 9.10 (Karmic).
Also has OOo 3.1.1 debs for Ubuntu 8.04 (Hardy) - unsupported.
```

Looks like you have done it correctly, but there are no packages in the PPA ?

---

