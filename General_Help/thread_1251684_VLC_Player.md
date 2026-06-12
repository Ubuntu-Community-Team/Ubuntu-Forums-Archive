---
title: "VLC Player"
date: 2009-08-28
forum: General Help
---

### Post by dileepchacko on 2009-08-28
please help me to install VLC player in UBUNTU 9.10

---

### Post by rhythmiccycle on 2009-08-28
easy, just go to add/remove in the applications menu (top left)

set the drop down "show" to "All available applications"

then type VLC in the search box

wait a moment (don't press any thing)

then check the vlc check box

hit the "apply changes" button

enter password

wait, and when its done, "close"


most programs can be found and installed this way.

i like VLC too, sometimes the default media player doesn't cut it.

---

### Post by sahabcse on 2009-08-28
open the terminal, then enter

#sudo apt-get install vlc

---

### Post by dj-toonz on 2009-08-28
the version in the 9.10 ubuntu repos is still the beta version if you do want the final version of VLC i've got a PPA for it which is [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc). hope that helps

---

### Post by rhythmiccycle on 2009-08-29
> **dj-toonz said:**
> the version in the 9.10 ubuntu repos is still the beta version if you do want the final version of VLC i've got a PPA for it which is [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc). hope that helps

i tried adding the sources:
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 

in system->admin-> software sources

and i get the error message:
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D


---

### Post by abhilashm86 on 2009-08-29
try using * after a package, as it also installs dependencies, its better to use synaptic package for begineers as it will take care of dependencies:)
```
sudo apt-get install vlc*
```

---

### Post by jocko on 2009-08-29
> **abhilashm86 said:**
> try using * after a package, as it also installs dependencies, its better to use synaptic package for begineers as it will take care of dependencies:)
```
sudo apt-get install vlc*
```
apt-get takes care of dependencies as well, no need for the *. Actually vlc* means "all packages with names containing something which is similar to 'vlc'". That not only means all packages with "vlc" in their names, but also all packages with "vl" in their names (I don't understand why, but this is what apt-get does...). Many packages that are installed with vlc* are completely unnecessary (like vlc debug and development packages and vlc plugins that most people don't need) and some are in no way related to vlc at all. Plus it will draw all the dependencies of all those unnecessary packages...

---

### Post by keastes on 2009-08-29
just search vlc in synaptic package manager thats how i got it the only reason i dont use it now is its to heavy for my pentium 3 to do anything else at the same time

access synaptic by either applications>system>synaptic package manager or system>synaptic package manager.

hope that helps

---

### Post by fluffman86 on 2009-08-29
> **rhythmiccycle said:**
> i tried adding the sources:
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 

in system->admin-> software sources

and i get the error message:

Did you add his signing key? 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678
```
where the numbers are the key you need to add.

---

### Post by rhythmiccycle on 2009-08-29
> **fluffman86 said:**
> Did you add his signing key? 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678
```
where the numbers are the key you need to add.

i ran the code in a terminal, and get:
```

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678
[sudo] password for mike: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 12345678
gpg: requesting key 12345678 from hkp server keyserver.ubuntu.com
gpg: key 12345678: public key "Artemis <artemis@olympos.god>" imported
gpg: Total number processed: 1
gpg:               imported: 1


```

then i went back to the software sources and still get the error

---

### Post by P4man on 2009-08-29
Just to be clear, this:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY D739676F7613768D

is a warning, not an error. you can still install your stuff, even though the packages can't be verified.  It will just prompt you a second time to ask if you are sure.

(thats not to say you shouldnt try fixing it)

---

