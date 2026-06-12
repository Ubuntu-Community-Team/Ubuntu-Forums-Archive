---
title: "Failed to download repository information (firefox)"
date: 2011-03-21
forum: General Help
---

### Post by langmarp on 2011-03-21
after uninstalling Namoroka i have the following issue with the updates

my update manager only downloads stable releases and only includes firefox stable updates

W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

please, help me out...
Thanks!

---

### Post by plucky on 2011-03-21
> **langmarp said:**
> after uninstalling Namoroka i have the following issue with the updates

my update manager only downloads stable releases and only includes firefox stable updates

W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

please, help me out...
Thanks!

There is no Maverick distribution for that PPA,which is why you are getting the 404 error. See [Here](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/)

Open Software Sources and delete the PPA as a source should fix your problem.

Good Luck

---

### Post by langmarp on 2011-03-22
I have changed to 
[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main

is this correct?

no error message any more :)
thanks!

---

### Post by plucky on 2011-03-22
> **langmarp said:**
> I have changed to 
[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main

is this correct?

no error message any more :)
thanks!

Are you running Lucid? 

If so then that is ok,but if you are running Maverick,then get rid of it as it is not a good idea to mix repositories between different releases.

Good Luck

---

### Post by langmarp on 2011-03-22
I run maverick...

than how should I solve this? what should I add to the repository?

---

### Post by plucky on 2011-03-22
Why do you need the PPA?

As you are running Maverick,all the updates are probably in the Ubuntu repositories anyway.

Open Software Sources and delete that PPA is the way to get rid of it.

If you need a later version of Firefox,then you will have to search on Launchpad to see if the Mozilla-team have a PPA for the latest version of Firefox.

Good Luck

---

### Post by langmarp on 2011-03-22
Than I just delete mozilla from ppa

thanks for clarifying!

---

