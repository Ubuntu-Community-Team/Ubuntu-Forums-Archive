---
title: "Can't use apt at all"
date: 2012-07-31
forum: General Help
---

### Post by buee on 2012-07-31
I get the following whenever I try to do anything with apt or dpkg:

```
Preconfiguring packages ...
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.8.6-1ubuntu2.1 cannot be configured because libgnutls26:amd64 is in a different version (2.10.5-1ubuntu3)
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.10.5-1ubuntu3 cannot be configured because libgnutls26:i386 is in a different version (2.8.6-1ubuntu2.1)
Errors were encountered while processing:
 libgnutls26:i386
 libgnutls26
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm running 12.04 x64 Desktop.

I've searched and have tried all sorts of replies, such as apt-get dist-upgrade -f.  That ends up throwing the error you see above.

---

### Post by kansasnoob on 2012-07-31
Try:

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo dpkg --configure -a
```

Then see how apt acts.

---

### Post by houseworkshy on 2012-07-31
apt-get dist-upgrade -f. would try to take you up to the latest version of Ubuntu, that may cause problems.  I think that the graphic installers use apt-get anyway so  ... hum.    There is also aptitude which may even be able to reinstall apt-get.  "man aptitude" in the terminal will take you to aptitudes manual page for details on how it works.

---

### Post by buee on 2012-07-31
```
root@nas2:~# apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
root@nas2:~# apt-get clean
root@nas2:~# dpkg --configure -a
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.10.5-1ubuntu3 cannot be configured because libgnutls26:i386 is in a different version (2.8.6-1ubuntu2.1)
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.8.6-1ubuntu2.1 cannot be configured because libgnutls26:amd64 is in a different version (2.10.5-1ubuntu3)
Errors were encountered while processing:
 libgnutls26
 libgnutls26:i386
root@nas2:~# apt-get dist-upgrade -f

```

dist-upgrade -f downloads a bunch of stuff, then outputs:

```
mini-client all 0.7.2+bzr57-0ubuntu1 [17.9 kB]
Fetched 213 MB in 2min 8s (1,661 kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.8.6-1ubuntu2.1 cannot be configured because libgnutls26:amd64 is in a different version (2.10.5-1ubuntu3)
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.10.5-1ubuntu3 cannot be configured because libgnutls26:i386 is in a different version (2.8.6-1ubuntu2.1)
Errors were encountered while processing:
 libgnutls26:i386
 libgnutls26
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Cheesehead on 2012-07-31
> **buee said:**
> Preconfiguring packages ...
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.8.6-1ubuntu2.1 cannot be configured because libgnutls26:amd64 is in a different version (2.10.5-1ubuntu3)

You seem to be trying to install the i386 version of a package instead of the amd64 version.

Do you recall what you were trying to do when this started?

---

### Post by buee on 2012-07-31
> **Cheesehead said:**
> You seem to be trying to install the i386 version of a package instead of the amd64 version.

Do you recall what you were trying to do when this started?

I did the distribution upgrades from 10.04 -> 10.10 -> 11.04 -> 11.10 -> 12.04.  Rebooted, nothing since (a couple weeks ago).  I just tried to update the system a couple days ago and have been working to get rid of these errors ever since.

---

### Post by houseworkshy on 2012-08-01
Searching for libgnutls26:i386 brings up a lot on google much of which is associated with borked distribution upgrades and a broken apt-get 
This one, which ended up easily solved, may be of interest

 [http://www.linuxquestions.org/questions/ubuntu-63/e-internal-error-no-file-name-for-libss2-messing-up-apt-get-948017/](http://www.linuxquestions.org/questions/ubuntu-63/e-internal-error-no-file-name-for-libss2-messing-up-apt-get-948017/)

If the last command posted in the quoted post doesn't do it perhaps concider a backup and reinstall.  Distribution upgrades are a great idea but frequently cause problems,  clean installs of new versions are generally less troublesome.

---

### Post by buee on 2012-08-01
> **houseworkshy said:**
> Searching for libgnutls26:i386 brings up a lot on google much of which is associated with borked distribution upgrades and a broken apt-get 
This one, which ended up easily solved, may be of interest

 [http://www.linuxquestions.org/questions/ubuntu-63/e-internal-error-no-file-name-for-libss2-messing-up-apt-get-948017/](http://www.linuxquestions.org/questions/ubuntu-63/e-internal-error-no-file-name-for-libss2-messing-up-apt-get-948017/)

If the last command posted in the quoted post doesn't do it perhaps concider a backup and reinstall.  Distribution upgrades are a great idea but frequently cause problems,  clean installs of new versions are generally less troublesome.

I tried it, but alas, no joy:

```
root@nas2:/media/NAS2/base/TBD# dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libgnutls26          the GNU TLS library - runtime library
 libgnutls26:i386     the GNU TLS library - runtime library

root@nas2:/media/NAS2/base/TBD# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgnutls26 libgnutls26:i386
Suggested packages:
  gnutls-bin gnutls-bin:i386
The following packages will be upgraded:
  libgnutls26 libgnutls26:i386
2 upgraded, 0 newly installed, 0 to remove and 183 not upgraded.
2 not fully installed or removed.
Need to get 0 B/907 kB of archives.
After this operation, 242 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.8.6-1ubuntu2.1 cannot be configured because libgnutls26:amd64 is in a different version (2.10.5-1ubuntu3)
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.10.5-1ubuntu3 cannot be configured because libgnutls26:i386 is in a different version (2.8.6-1ubuntu2.1)
Errors were encountered while processing:
 libgnutls26:i386
 libgnutls26
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nas2:/media/NAS2/base/TBD# dpkg --configure --pending
dpkg: error processing libgnutls26 (--configure):
 libgnutls26:amd64 2.10.5-1ubuntu3 cannot be configured because libgnutls26:i386 is in a different version (2.8.6-1ubuntu2.1)
dpkg: error processing libgnutls26:i386 (--configure):
 libgnutls26:i386 2.8.6-1ubuntu2.1 cannot be configured because libgnutls26:amd64 is in a different version (2.10.5-1ubuntu3)
Errors were encountered while processing:
 libgnutls26
 libgnutls26:i386

```

---

### Post by buee on 2012-08-01
I managed to download libgnutls26 from a random ubuntu mirror and dpkg let me install it.  I ran all the above commands again and I can now use apt again.  No idea what happened, but I'm just glad it's fixed.

---

