---
title: "Broken Package Error...help ASAP please!"
date: 2010-01-30
forum: General Help
---

### Post by oxf on 2010-01-30
Let me start out by stating that I performed this upgrade on my desktop yesterday without problem so I dont know why I cant do the same on my laptop today, but thats another question..

Right now I want to resolve this on my laptop. I'm trying to upgrade to Firefox 3.6 on my laptop. Folling instructions on another thread I added the following to the System>Admin>Software Sources>Third Party Software  :

> **Leppie said:**
> use the mozilla daily ppa, the repos are:
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main 
```

Then when I went into Synaptic to add FF3.6 it does that but I get an error that results in two broken packages, i.e. Firefox 3.6.2 and Firefox 3.5 branding. I believe this is related to the error I got earlier telling me I was missing a Public Key for one of the PPA sources.

So PLEASE can someone tell me how to resolve this, get the public key and whatever? As of now I have a non functiional browser on the laptop and having to post this through the other PC. I'll give more info if needed.

Thanks

---

### Post by gradinaruvasile on 2010-01-30
Its not related to the public key at all.
open a terminal and type (copy-paste):

sudo apt-get install -f


I would say to just d/l the generic linux build from the site, it works perfectly well and you will get out of this dependency problem.

PS If you need a working browser fast on your PC: 
In a terminal:

sudo apt-get install midori

You will find it in the network menu. Midori is a small and fast browser.

---

### Post by oxf on 2010-01-30
> **gradinaruvasile said:**
> Its not related to the public key at all.
open a terminal and type (copy-paste):

sudo apt-get install -f


I would say to just d/l the generic linux build from the site, it works perfectly well and you will get out of this dependency problem.

Well that give problems too! It says its going to install Firefox branding. Then returns errors:
first   "without verification? Y/N?"
then   "trying to overwrite /usr/share/applications/firfox.desktop, which is also in Firefox-3.0-branding"

Tells me "error encounterd whjile processing in firefox branding 3.6.2":confused:

---

### Post by gradinaruvasile on 2010-01-30
Oh man... Just uninstall the firefox-3.0-branding... Or the whole firefox 3.0 package. 

I just downloaded the latest firefox from the mozilla's site, unpacked it in /opt/ and made a link to the /usr/bin/firefox and firefox-3.5.

And dont worry about the verification thing now. But next time you play around with repositories make sure you read the whole installation instructions, including the security keys.

---

### Post by oxf on 2010-01-30
> **gradinaruvasile said:**
> Oh man... Just uninstall the firefox-3.0-branding... Or the whole firefox 3.0 package. 

I just downloaded the latest firefox from the mozilla's site, unpacked it in /opt/ and made a link to the /usr/bin/firefox and firefox-3.5.

And dont worry about the verification thing now. But next time you play around with repositories make sure you read the whole installation instructions, including the security keys.

Yes I'm removing right now and will try again!
Thanks!

---

### Post by oxf on 2010-01-30
OK you are saying that the public key error msg has nothing to do with this problem? I never got that on my Desktop and never had any problems installing it from the ppa's

I just removed all FF completely and reinstalled again and now seem to have Namoroka working.
Maybe its time for my bed!

---

### Post by theozzlives on 2010-01-30
Namoroka is prolly the codename for the new FF. Why you guys insist on installing before it's ready is beyond me.

---

