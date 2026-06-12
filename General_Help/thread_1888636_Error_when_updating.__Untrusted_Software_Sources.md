---
title: "Error when updating.  Untrusted Software Sources?"
date: 2011-11-29
forum: General Help
---

### Post by jrisreal on 2011-11-29
I've been searching google for a couple weeks for this.  I get this error every time I try to perform an update and also sometimes when I download certain applications.  I went into the software sources and checked any option that looked like it could be the problem, but nothing has worked.  When I was running 10.04 on my old laptop, I had the same problem, but eventually solved it...but it is not happening on this one.  I am running 11.10 Unity 64-bit.

---

### Post by jerrrys on 2011-12-01
open a terminal and enter:

sudo apt-get update

and post any errors

---

### Post by oldos2er on 2011-12-01
The info you need is in that 'Details' button.

---

### Post by jrisreal on 2011-12-01
no it isn't.  it just tells me which update is not trusted...

Here are any errors I found in the terminal:
> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                   
  404  Not Found
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBDFA02B432BB368
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 87538FEDDF8063EB
W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


And I attached a new screenshot with the details tab opened.

---

### Post by oldos2er on 2011-12-02
To fix the NO_PUBKEY errors, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the alphanumeric string shown in the error.

The stebbins PPA has no support for oneiric, so I'd remove it. Same with " http://ppa.launchpad.net", there's no PPA named oneiric at that URL.

---

### Post by jrisreal on 2011-12-03
> **oldos2er said:**
> To fix the NO_PUBKEY errors, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the alphanumeric string shown in the error.

The stebbins PPA has no support for oneiric, so I'd remove it. Same with " http://ppa.launchpad.net", there's no PPA named oneiric at that URL.
I forgot to mention that I don't know all that much about Linux...but anyway, I couldn't find a 'stebbins' PPA in my sources.  And nearly every source starts with [http://ppa.launchpadnet](http://ppa.launchpadnet)

---

### Post by oldtimer7777 on 2011-12-03
> **jrisreal said:**
> I've been searching google for a couple weeks for this.  I get this error every time I try to perform an update and also sometimes when I download certain applications.  I went into the software sources and checked any option that looked like it could be the problem, but nothing has worked.  When I was running 10.04 on my old laptop, I had the same problem, but eventually solved it...but it is not happening on this one.  I am running 11.10 Unity 64-bit.

Use synaptic package manager instead to install packages. 

sudo apt-get install synaptic 
sudo synaptic

---

### Post by oldos2er on 2011-12-03
> **jrisreal said:**
> I forgot to mention that I don't know all that much about Linux...but anyway, I couldn't find a 'stebbins' PPA in my sources.  And nearly every source starts with [http://ppa.launchpadnet](http://ppa.launchpadnet)

PPAs are listed in /etc/apt/sources.list.d/
If you run **gksu software-properties-gtk** in a terminal, it should be in the 'Other Software' tab.

---

### Post by jrisreal on 2011-12-04
> **oldos2er said:**
> PPAs are listed in /etc/apt/sources.list.d/
If you run **gksu software-properties-gtk** in a terminal, it should be in the 'Other Software' tab.
Thank you.  I guess it was there before, I just didn't see it.

But yeah I thought Synaptic came preinstalled with Ubuntu.  It did in 10.04, why not now?

---

### Post by oldos2er on 2011-12-04
Synaptic was removed from 11.10's default installation to, if I'm not mistaken (and I could be) make room on the CD for other software; same as aptitude was removed from 11.04's default install.

---

