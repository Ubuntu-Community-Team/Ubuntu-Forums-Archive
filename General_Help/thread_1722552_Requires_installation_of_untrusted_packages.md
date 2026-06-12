---
title: "Requires installation of untrusted packages"
date: 2011-04-05
forum: General Help
---

### Post by prettymess on 2011-04-05
When I try and update I get this error message:

"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Details: libgpod-common libgpod4 libimobiledevice-utils libimobiledevice1 libusbmuxd1 usbmuxd"

Any help? (I'm using 10.10, by the way)

---

### Post by 23dornot23d on 2011-04-05
You have maybe added a ppa at some point ...... for your mobile device (ipod) maybe .....

Its just warning you ............ 

( if everything is working ok - no real need to update them - your choice though )

More info on one of the files the link below .......

what is [libgpod4]("http://www.google.com/search?client=ubuntu&channel=fs&q=libgpod4&ie=utf-8&oe=utf-8")

---

### Post by Frogs Hair on 2011-04-05
Open the terminal and run the code and try to update again .```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

---

### Post by rogerdg on 2011-04-05
10.10 seems to have an update problem.  On my computer I ran the following
```

sudo apt-get update

```
until the apt-get no longer reported error messages.  Then I ran update manager and successfully updated my computer.

I have been trying for about 2 weeks to resolve the problem, but apt-get update was not retrieving the information necessary to fix the problem.  I was able to successfully run apt-get update and then run update manager today.

---

### Post by prettymess on 2011-04-06
I tried sudo apt-get update and it came up with this error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EA3A911D48B8E25

---

### Post by oldos2er on 2011-04-06
To install the key, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4EA3A911D48B8E25
```

---

### Post by prettymess on 2011-04-06
> **23dornot23d said:**
> You have maybe added a ppa at some point ...... for your mobile device (ipod) maybe .....

Its just warning you ............ 

( if everything is working ok - no real need to update them - your choice though )

More info on one of the files the link below .......

what is [libgpod4]("http://www.google.com/search?client=ubuntu&channel=fs&q=libgpod4&ie=utf-8&oe=utf-8")
Tried it, but it didn't work:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4EA3A911D48B8E25
gpg: requesting key D48B8E25 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by oldos2er on 2011-04-06
> **prettymess said:**
> 
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

That seems to happen often. Wait twelve hours or so, and try again.

---

### Post by prettymess on 2011-04-24
Edit: Nevermind, i think it might have worked.

---

