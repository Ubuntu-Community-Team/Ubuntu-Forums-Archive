---
title: "Bitcoins"
date: 2012-03-22
forum: General Help
---

### Post by chesspro on 2012-03-22
[http://bitcoin.org/](http://bitcoin.org/)

I want to download the latest version (0.5.3.1) for Ubuntu 11.04 (Natty) but I keep getting the following message...

```
Err http://deb.torproject.org natty Release.gpg
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Ign http://deb.torproject.org natty Release
Ign http://deb.torproject.org natty/main Sources/DiffIndex
Ign http://deb.torproject.org natty/main i386 Packages/DiffIndex
Ign http://deb.torproject.org natty/main TranslationIndex
Err http://deb.torproject.org natty/main Sources
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err http://deb.torproject.org natty/main i386 Packages
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err http://deb.torproject.org natty/main Translation-en_CA
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err http://deb.torproject.org natty/main Translation-en
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/natty/Release.gpg  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/natty/main/source/Sources  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/natty/main/binary-i386/Packages  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/natty/main/i18n/Translation-en_CA  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/natty/main/i18n/Translation-en  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```Please help.

---

### Post by QIII on 2012-03-22
You may have to update your source.  I suspect the problem may lie here...

**Not Found**

 The requested URL /torproject.org/dists/natty/main/i18n/Translation-en was not found on this server.
  Apache/2.2.16 (Debian) Server at deb.torproject.org Port 80

---

### Post by chesspro on 2012-03-24
I don't know what that means, QIII.  Could you give me step-by-step instructions on how to update the source?  

Thank you for all your help.

---

### Post by BkkBonanza on 2012-07-28
Probably ancient history now but I just came across this.

Best thing is for you to add the Bitcoin PPA so it gets updated from the maintained repository. One way to do this is the command, 

sudo add-apt-repository ppa:bitcoin/bitcoin

You can also add the same info manually using Synaptics. Select Settings, Repositories, Other Software and Add. Enter this line,

deb [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) natty main

Either way you can then update and/or install.

CmdLine:

sudo apt-get update
sudo apt-get install bitcoin

Synaptics:

Click Reload.
Search for "bitcoin", select it and click Apply.

---

