---
title: "update vbox bzip2 error"
date: 2009-12-06
forum: General Help
---

### Post by alanwalterthomas on 2009-12-06
I get the text below from sudo apt-get update, I'm still able to upgrade other packages, just not VBox:

...
Get:3 [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages [1,538B]                                                                     
20% [3 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting for headers] [2 Release 12165/66.0kB 18%]
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                                                            
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
...             
Fetched 70.1kB in 1min 11s (988B/s)
W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/binary-i386/Packages.bz2](http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

I tried sudo apt-get install bzip2recover but it wasn't found.
Any help is very welcome.

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
The package is corrupted. Re-download and try again.

---

### Post by alanwalterthomas on 2009-12-07
How? I tried reinstalling virtualbox from synaptic but that didn't help. It reinstalled, I checked for updates, same error, & I'm still stuck with virtualbox 3.0.x, when I should be getting 3.1.
So, how can I get apt-get back in shape to download this update as it should?

Thanks,

---

### Post by Sin@Sin-Sacrifice on 2009-12-09
It's using the same package you downloaded initially so use ```
sudo apt-get remove --purge virtualbox-ose
``` Then ```
sudo apt-get install virtualbox-ose
```

---

### Post by alanwalterthomas on 2009-12-09
Ok, thanks for the purge tip.
I'm not using the OSE edition. I have this in my software sources:
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
& I still got this when I tried to update my packages (before trying to reinstall):

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/binary-i386/Packages.bz2](http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

What's going on?

---

### Post by synapsys on 2009-12-09
Have you already added the sun public key for apt-secure?

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

---

### Post by alanwalterthomas on 2009-12-11
.

---

### Post by alanwalterthomas on 2009-12-11
HA! I figured it out.
I was using apt-cacher-ng to keep copies of packages so I wouldn't have to re-download them to install on other computers.
I had to go to the apt-cacher-ng maintenance page ([http://localhost:3142/acng-report.html](http://localhost:3142/acng-report.html)) & check "Force the download of index files (even having fresh ones)" then click "Start scan and/or expiration". I waited a while, updated, & voila! Virtualbox 3.1 installed beautifully.

---

