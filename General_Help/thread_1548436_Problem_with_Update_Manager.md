---
title: "Problem with Update Manager?"
date: 2010-08-08
forum: General Help
---

### Post by binarylife on 2010-08-08
So I'm using Ubuntu 10.04 lycid 64bit , and recently everything was more than great, but today i tried to check for updates using the update manager but it couldn't fetch the sources ! it gives me a MSG :
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I tried sudo apt-get update & upgrade , but it gives me the same problem ,BTW I'm new to linux system.
but I tried to change the source.list to it's default using Google for sure .. but still have the problem .
so is there any possible way to solve this problem ? Can I restore source.list to it's default using terminal or anything else ?
and another question :Could I restore Ubuntu to it's original default settings?
Thanks in Advance , And I'm ready to learn :) ...

---

### Post by binarylife on 2010-08-08
Also i have problem with pidgin internet messenger it cloes by itself.. so I tried the update manager which failed...Please help I'm Stuck !!

---

### Post by claracc on 2010-08-08
You go to the medibuntu ppa [https://launchpad.net/~medibuntu-maintainers/+archive/ppa](https://launchpad.net/~medibuntu-maintainers/+archive/ppa) (you select the right one for your 64 lucid system), and in the part with technical details of this ppa you have a line with signing key, click on what is this? and there appear the rules to add this ppa to your sources list and also the way to fetch the ppa key.

---

### Post by dino99 on 2010-08-08
> **binarylife said:**
> So I'm using Ubuntu 10.04 lycid 64bit , and recently everything was more than great, but today i tried to check for updates using the update manager but it couldn't fetch the sources ! it gives me a MSG :
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I tried sudo apt-get update & upgrade , but it gives me the same problem ,BTW I'm new to linux system.
but I tried to change the source.list to it's default using Google for sure .. but still have the problem .
so is there any possible way to solve this problem ? Can I restore source.list to it's default using terminal or anything else ?
and another question :Could I restore Ubuntu to it's original default settings?
Thanks in Advance , And I'm ready to learn :) ...

[COLOR="Blue"]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783[/COLOR]

---

