---
title: "Lucid will not Update Firefox"
date: 2011-09-12
forum: General Help
---

### Post by ventrical on 2011-09-12
Lucid will not update firefox. 

Anybody?

---

### Post by Karlchen on 2011-09-12
Hello, ventrical.

I suggest to update the Synaptic package information list, because by the time you started your thread Firefox 3.6.22 was the latest Firefox version which Canonical offered to Lucid users, no longer 3.6.21.
So update the package information list and try to update to Firefox 3.6.22.

HTH,
Karl
--
[SIZE=2]P.S.:
In case you wish to replace Firefox 3.6.x by the latest version offered by Mozilla, v6.02 at the time of writing this, then have a closer look at this webpage: [**Ubuntuzilla**]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation"). Ubuntuzilla will allow you to download and install the latest Mozilla releases of Firefox, Thunderbird and/or SeaMonkey on Lucid Lynx.[/SIZE]

---

### Post by Frogs Hair on 2011-09-12
Another method is to enter the following commands in the terminal _one at a time_

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ventrical on 2011-09-15
> **Frogs Hair said:**
> Another method is to enter the following commands in the terminal _one at a time_

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```


Nice work !!

Thanks for that report.

It worked great !

:)

---

### Post by sonhadorpr on 2011-11-14
Hello guys!
I followed the step-by-step instructions on the command line, and I was able to upgrade to 7.0.1. on Ubuntu 10.04.3 LTS.
THANK YOU VERY MUCH!!!
I'll wait for later, until the next LTS to upgrade, not really care for the other FireFoxes...but I do believe in 11.10 they are automatically upgrading (almost) everything, so the upgrade to 12.04 should also include the newest firefox... am I correct?
Thanx again!

---

### Post by dcstar on 2011-11-14
> **sonhadorpr said:**
> 
...........
I'll wait for later, until the next LTS to upgrade, not really care for the other FireFoxes...but I do believe in 11.10 they are automatically upgrading (almost) everything, so the upgrade to 12.04 should also include the newest firefox... **am I correct**?


No, Ubuntu releases are only supported with the version of apps packaged with the original release. The only updates are Security Updates and not version updates.

You *might* get later versions by enabling the Backports and Proposed Repositories or adding 3rd party Repositories.

---

