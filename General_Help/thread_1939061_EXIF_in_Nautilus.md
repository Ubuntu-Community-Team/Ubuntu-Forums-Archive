---
title: "EXIF in Nautilus"
date: 2012-03-10
forum: General Help
---

### Post by davidkazuhiro on 2012-03-10
I want to get EXIF data to show in nautilus so that I can sort my photos by the date captured.

I found nautilus-columns via [this article]("http://www.webupd8.org/2010/10/music-and-exif-metadata-information-in.html") and tried to install it but had no luck. Here's what I did.

```

$ sudo add-apt-repository ppa:nilarimogard/webupd8
[...output ommitted...]
$ sudo apt-get update
[...output ommitted...]
$ sudo apt-get install nautilus-columns
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package nautilus-columns

```

Hrm, so we take a look to see if the repository is actually there.

```

$ cat /etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu oneiric main
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu oneiric main

```

It's there. Maybe a previous version works?

```

$ sudo sed -i -e "s/oneiric/natty/g" /etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list
$ sudo apt-get update
[...output ommitted...]
$ sudo apt-get install nautilus-columns
[...Installation successful, no errors or warnings]

```

The installation works! However when I launch nautilus and go Edit->Preferences->List Columns, this list of available columns is no different than before I installed (see attached image).

And yes, I did do

```

nautilus -q

```

Just to be sure.

Has anybody gotten this working on oneiric? If it doesn't work on oneiric, then is there some other option?

```

$ lsb_release -d && arch && nautilus --version
Description:	Ubuntu 11.10
i686
GNOME nautilus 3.2.1

```

---

### Post by dandaman96 on 2012-04-04
After four or five hours on google, I can't find anything to address this in 11.10 (oneiric).  This is something so simple, I don't understand why nautilus does not have this functionality by default.

---

