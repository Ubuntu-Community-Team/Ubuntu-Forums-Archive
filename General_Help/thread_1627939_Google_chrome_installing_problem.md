---
title: "Google chrome installing problem"
date: 2010-11-22
forum: General Help
---

### Post by molykkutti on 2010-11-22
I tried to install Google chrome in ubuntu  
when i tried to  set up key with Code:

wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
 
I got the following error .. 

W: GPG error: [http://dl.google.com]("http://dl.google.com/") stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

Please help .. i dont know how to solve this crisis ...

---

### Post by Soul-Sing on 2010-11-22
please try chromium, it is in synaptic packagemanager.
(chromium=chrome does the same thing, but is opensource.)

---

### Post by rituparnakashyap on 2010-11-22
I download the dev package from google download and it working fine with me !!:popcorn:

---

### Post by garvinrick4 on 2010-11-22
##You have the 2 choices chromium stable from regular packages.
```
sudo apt-get install chromium-browser
```
##Or the ppa with the unstable chromium where you get updated dialy.
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
#site above is self explanitory:

---

### Post by garvinrick4 on 2010-11-22
> **rituparnakashyap said:**
> I download the dev package from google download and it working fine with me !!:popcorn: 32 bit and 64 are 2 different animals so be sure you ask which they are using when an install question.

---

### Post by mika0110 on 2010-11-22
1)You should remove Chrome.
2)try portablelinuxapps.org and download chrome portable.
Then,click right mouse ->properties->permission (tick execute)
3)Run by double click.

Havefun

---

### Post by amite on 2010-11-22
USE THIS LINK  to direct install : [http://www.google.com/chrome](http://www.google.com/chrome)

---

