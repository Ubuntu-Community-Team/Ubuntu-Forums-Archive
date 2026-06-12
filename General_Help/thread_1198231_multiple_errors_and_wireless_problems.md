---
title: "multiple errors and wireless problems"
date: 2009-06-27
forum: General Help
---

### Post by MCMalkemus on 2009-06-27
When I try to upgrade, this appears: 

                                 W: GPG errW: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791 or: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE  
 W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991  
 
I believe it began after I started to download Ubuntu Studio and aborted the download halfway through, but this is just a guess.

It could also have occurred after I used computer janitor. 

Oddly, my wireless will not work anymore... it shows all the Networks, but the browsers just show blank pages and "done". The wired networks work fine...

Thanks for any insights.  ](*,)

HP dv8000 notebook ubuntu 9.04 with VirtualBox OSE running XP as a guest.

---

### Post by raymondh on 2009-06-27
> **MCMalkemus said:**
> When I try to upgrade, this appears: 

                                 W: GPG errW: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791 or: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE  
 W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991  
 
I believe it began after I started to download Ubuntu Studio and aborted the download halfway through, but this is just a guess.

It could also have occurred after I used computer janitor. 

Oddly, my wireless will not work anymore... it shows all the Networks, but the browsers just show blank pages and "done". The wired networks work fine...

Thanks for any insights.  ](*,)

HP dv8000 notebook ubuntu 9.04 with VirtualBox OSE running XP as a guest.

Let's try something about those "no pubkey" errors :)  

You need to have internet access, so maybe use an ethernet cable in the meantime.

Here's the format.  You have to do for each error with its' own pub key number.  I will start by using the first pubkey listed.

In terminal (applications > accessories), type and enter one at a time

```
gpg --keyserver subkeys.pgp.net --recv 033431536A423791
gpg --export --armor 033431536A423791 | sudo apt-key add - 
sudo apt-get update
```

You'll need to do it for each and every pubkey you see.  Just change the pubkey combination.  As stated, I already added the first pubkey (ending 23791).

After everything is done, run

```
sudo apt-get update
sudo apt-get upgrade
```

Now, if you prefer to work on wireless first .... have you installed anything different ... like a new kernel perhaps?  If so, can you access the older kernel and see if wifi works?  If it does, we may have to re-install drivers.  Have you activated drivers in system > admin > hardware drivers?

In terminal, kindly post output of

```
lspci -v
iwconfig
```

This link may help or give you clues regarding wireless:

[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Good luck.

---

### Post by MCMalkemus on 2009-06-28
Big thanks Raymond, worked perfectly!:popcorn::guitar:\\:D/

---

### Post by raymondh on 2009-06-28
> **MCMalkemus said:**
> Big thanks Raymond, worked perfectly!:popcorn::guitar:\\:D/

Am glad you got it working.  Big Welcome as well. 

happy ubuntu-ing.

---

