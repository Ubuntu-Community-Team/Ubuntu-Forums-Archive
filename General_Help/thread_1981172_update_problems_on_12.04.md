---
title: "update problems on 12.04"
date: 2012-05-16
forum: General Help
---

### Post by gestrich on 2012-05-16
Hi,

I'm having trouble updating in Ubuntu 12.04. Every time I check using the update manager (or the terminal), I get following message:

W:GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783, W:Failed to fetch [http://??archive.canonical.com/dists/precise/Release.gpg](http://??archive.canonical.com/dists/precise/Release.gpg)  Something wicked happened resolving '??archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://??archive.canonical.com/dists/precise/partner/source/Sources](http://??archive.canonical.com/dists/precise/partner/source/Sources)  Something wicked happened resolving '??archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://??archive.canonical.com/dists/precise/partner/binary-i386/Packages](http://??archive.canonical.com/dists/precise/partner/binary-i386/Packages)  Something wicked happened resolving '??archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://??archive.canonical.com/dists/precise/partner/i18n/Translation-en](http://??archive.canonical.com/dists/precise/partner/i18n/Translation-en)  Something wicked happened resolving '??archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Any help would be much appreciated!

---

### Post by kanikilu on 2012-05-16
Are those question marks actually in the error message? That doesn't seem right...

Can you post the contents of /etc/apt/sources.list? Also, since you mention mediabuntu, there may be more repos listed in /etc/apt/sources.list.d/.

Also, please put any output in CODE tags on the forum so it's easier for people to read.

---

### Post by gestrich on 2012-05-16
Thanks for taking an interest in my problem!

Just to be clear, the error message I posted below comes from the update manager, and the question marks are in it. It struck me as strange, too.

In /etc/apt/sources.list are the following repositories

```

deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted


deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted


deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe


deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse


deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-security multiverse


# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


deb http://extras.ubuntu.com/ubuntu precise main
deb http: ??archive.canonical.com/ precise partner
deb-src http: ??archive.canonical.com/ precise partner
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://repository.spotify.com stable non-free

```

I've noticed that the question marks appear here, too.

/etc/apt/sources.list.d contains these:

```

deb http://packages.medibuntu.org/ precise free non-free 
# deb-src http://packages.medibuntu.org/ precise free non-free

``` 

hope I've managed to get the code tags right this time.

---

### Post by kanikilu on 2012-05-16
You got the code tags right, thanks :-)

Those questions marks in the main sources.list file are definitely not right. Change these lines:

```
deb http: ??archive.canonical.com/ precise partner
deb-src http: ??archive.canonical.com/ precise partner
```

to this:

```
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
```

Use a text editor like vi or nano, or if you prefer GUI, gedit:

```
gksu gedit /etc/apt/sources.list
```

Enter your password when prompted, change the offending lines, and then save and close the file. Run ```
sudo apt-get update
``` again.

Also, on the medibuntu issue, have you added the GPG key? If not, follow the instructions here:

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by gestrich on 2012-05-17
It's worked, and the updates are running as they should now.

Thank you very much for your fast and helpful replies!

---

