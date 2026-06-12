---
title: "Cant install security updates"
date: 2010-01-02
forum: General Help
---

### Post by gareththomasnz on 2010-01-02
Just a week or so back when i run update manager I can no longer install any security updates - its all grey in the tick boxes.

How do I remedy this ?

---

### Post by drs305 on 2010-01-02
A simple first step would be to try to reinitialize the security repositories. Open Synaptic or Software Sources, Settings, Repositories, Updates. Untick the "karmic-security" box (or your version) and then reselect it and press "Reload". That should get Synaptic to update the security packages available, which might solve things.

You might also try running this from the terminal to see if any error messages are generated:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by warfacegod on 2010-01-02
I don't know if your issue is related to this not not but the timing is suspect. We haven't got a solution yet but maybe if the thread gets big enough, someone will notice.


[http://ubuntuforums.org/showthread.php?t=1370343]("http://ubuntuforums.org/showthread.php?t=1370343")

---

### Post by gareththomasnz on 2010-01-03
Thanks I'll look into it this evening - don't like not having a secure system

mine **_does show_** a list of updates but says they cant be installed. Another annoyance is some time ago I was going to update from the CD but chose not to - now I always have this list of updates that are out of date from the CD

How do I delete the CD as a source ?

Getting this error when updating repositories:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFFGPG error: [http://lgp203.free.fr](http://lgp203.free.fr) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5D3F763EB8620CD6Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://blognux.free.fr/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://blognux.free.fr/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2010-01-03
> **gareththomasnz said:**
> How do I delete the CD as a source ?
Open Synaptic: Settings, Repositories, Ubuntu Software. Untick the Hardy CDROM  listed in the lower pane. If you have any CDs listed in the "Third Party/Other Software" tab, you can do the same.

> 
Failed to fetch [http://blognux.free.fr/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://blognux.free.fr/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found


Deselect this from the Third Party/Other Software tab.

These commands will import the keys for the GPG errors you are receiving:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 7D2C7A23BF810CD5 665F9AEFE1098513 60D11217247D1CFF 5D3F763EB8620CD6 && gpg --export --armor 7D2C7A23BF810CD5 665F9AEFE1098513 60D11217247D1CFF 5D3F763EB8620CD6 | sudo apt-key add -
```

---

### Post by gareththomasnz on 2010-01-03
trying this:

apt-get install bind9 bind9-host

---

