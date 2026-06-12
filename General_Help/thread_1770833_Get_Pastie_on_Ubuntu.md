---
title: "Get Pastie on Ubuntu?"
date: 2011-05-29
forum: General Help
---

### Post by SterlingM on 2011-05-29
Hi, I am trying to install pastie. All the places online said to do this script - 
sudo add-apt-repository ppa:hel-sheep/pastie && sudo apt-get update
sudo apt-get install pastieAnother had a sudo upgrade in the middle, but essentially just that script above. Whenever I do that, my terminal hangs at - 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 68B9B7F6B51298512D6B5A8993B9ADE3DE4CA452
gpg: requesting key DE4CA452 from hkp server keyserver.ubuntu.com

Eventually I crtl c and it looks like its installing, but then stops and says -

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 93B9ADE3DE4CA452

What does this mean and what do I need to go to fix it? Any help is appreciated.

---

### Post by SterlingM on 2011-05-29
bump

---

### Post by linuxinstalledfromhdd on 2011-05-29
sudo apt-get -f update

Then go to this page and try these instructions:

[http://www.webupd8.org/2010/06/pastie-gets-ubuntu-ppa.html](http://www.webupd8.org/2010/06/pastie-gets-ubuntu-ppa.html)

---

### Post by Frogs Hair on 2011-05-29
I just installed on 11.04 with this PPA and it appears to be the same PPA as 10.10.```
sudo add-apt-repository ppa:hel-sheep/pastie
sudo apt-get update
sudo apt-get install pastie
``` 

Try running this code and try the PPA again. ```
sudo apt-get update 
```

---

