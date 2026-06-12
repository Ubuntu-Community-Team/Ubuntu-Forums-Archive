---
title: "Can't install K9copy"
date: 2011-10-21
forum: General Help
---

### Post by geovino on 2011-10-21
when trying to install K9copy, I get this error:

Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric/non-free mencoder amd64 2:1.0~rc4.dfsg1+svn33713-1+medibuntu1
  404  Not Found
Failed to fetch [http://packages.medibuntu.org/pool/non-free/m/mplayer/mencoder_1.0~rc4.dfsg1+svn33713-1+medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/m/mplayer/mencoder_1.0~rc4.dfsg1+svn33713-1+medibuntu1_amd64.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
davek@dave-pch:~$ 

what is needed to install K9copy?

running Xubuntu 11.10 64bit

---

### Post by oldos2er on 2011-10-21
packages.medibuntu.org appears to be offline; not sure there's anything you can do about that.

---

### Post by geovino on 2011-10-21
> **oldos2er said:**
> packages.medibuntu.org appears to be offline; not sure there's anything you can do about that.

I'll wait a couple days and try again. Thanks.

---

### Post by ezsit on 2011-10-21
Try the suggestion given:
"maybe run apt-get update or try with --fix-missing?"

**apt-get install k9copy --fix-missing**

This just worked for me. Give it a shot.

---

### Post by geovino on 2011-10-21
sudo apt-get install k9copy --fix-missing

It worked for me too. 

Thanks. :)

---

### Post by POWMS on 2012-03-01
I found this after searching the forum for problems with K9copy.
After installing VLC 2.0 I lost K9. When I tried to re-install, and error showed required library files were missing and installation was aborted.
After installing "mencoder" from Synaptic I could then install K9.
I also uninstalled VLC and went back to the approved version for 11.10.
All works well now.
This may help anyone else with K9 problems.

---

