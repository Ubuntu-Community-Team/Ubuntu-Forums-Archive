---
title: "VirtualBox Fails to install"
date: 2009-10-27
forum: General Help
---

### Post by Monotoko on 2009-10-27
I cant seem to get VirtualBox working on 64-bit karmic, im at a loss of what to do, i download the AMD64 file from the virtualbox website, get the package installer up, start it, then it stops because of:

```
dpkg: unable to read filedescriptor flags for <package status and 
progress file descriptor>: Bad file descriptor
```

Anyone have any ideas what that means, and how it can be fixed?

Thank you
~Monotoko

---

### Post by alphaniner on 2009-10-27
I would check the md5 sum against the appropriate one linked to on the [VBox Downloads Page]("http://www.virtualbox.org/wiki/Linux_Downloads").

I might also suggest using the method on the same page (under the 'Debian-based Linux distributions' header) to allow VBox to be installed/updated through apt.

---

### Post by Monotoko on 2009-10-27
The md5sum is correct, and there is no virtualbox-3.0 in apt

---

### Post by alphaniner on 2009-10-27
The instructions to add version 3.0 to apt is on the VBox downloads page:

**Debian-based Linux distributions**

Add one of the following lines according to your distribution to your /etc/apt/sources.list:

```
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
deb http://download.virtualbox.org/virtualbox/debian gutsy non-free
deb http://download.virtualbox.org/virtualbox/debian dapper non-free
deb http://download.virtualbox.org/virtualbox/debian lenny non-free
deb http://download.virtualbox.org/virtualbox/debian etch non-free
deb http://download.virtualbox.org/virtualbox/debian sarge non-free
deb http://download.virtualbox.org/virtualbox/debian xandros4.0-xn non-free
```

The Sun public key for apt-secure can be downloaded here. You can add this key with

```
sudo apt-key add sun_vbox.asc
```

or combine downloading and registering:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

The key fingerprint is

```
AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
```

To install VirtualBox, do

```
apt-get install virtualbox-3.0
```

Note: Ubuntu users might want to install the dkms package (not available on Debian) to ensure that the VirtualBox host kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are properly updated if the linux kernel version changes during the next apt-get upgrade.

---

### Post by howefield on 2009-10-27
> **Monotoko said:**
> Anyone have any ideas what that means, and how it can be fixed?

This was an issue with Karmic Alpha 4 or 5, but seemed to get fixed.
[https://bugs.launchpad.net/vte/+bug/388953](https://bugs.launchpad.net/vte/+bug/388953)

If it is the same problem, installing with the terminal worked for me.

I think it was

```
sudo dpkg -i filename
```

---

