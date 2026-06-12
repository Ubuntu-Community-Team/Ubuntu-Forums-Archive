---
title: "Ubuntu 11.10: After adding a PPA the software doesn't show up in Synaptic"
date: 2012-02-21
forum: General Help
---

### Post by bdw on 2012-02-21
When I add a ppa, the software doesn't show up in either Synaptic, USC, or other package manager.  Here's an example with the recently released VLC 2.0:

```
sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
```

I then run:

```
sudo apt-get get install vlc
```

which results in the following error:

```
vlc is already the newest version.
```

I have to download and install the software manually from PPA site, then the software will be updateable if updates are released.

I saw this described [here]("http://askubuntu.com/questions/98412/i-add-a-ppa-but-the-software-does-not-show-up-in-ubuntu-11-10-updates-nor-softwa") at askubuntu.com but there doesn't seem to be a workaround.

It appears that this may be a bug, but is there a fix or a workaround?

---

### Post by dcstar on 2012-02-21
> **bdw said:**
> When I add a ppa, the software doesn't show up in either Synaptic, USC, or other package manager.  Here's an example with the recently released VLC 2.0:

```
sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
```

I then run:

```
sudo apt-get get install vlc
```

which results in the following error:

```
vlc is already the newest version.
```

I have to download and install the software manually from PPA site, then the software will be updateable if updates are released.
........

And how many Versions does **Synaptic** show for the package?

---

### Post by bdw on 2012-02-21
> **dcstar said:**
> And how many Versions does **Synaptic** show for the package?

Only one - VLC 2.0 should have been listed as upgradeable but only 1.1.4 was present.

---

