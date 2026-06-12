---
title: "error for when I do apt-get..."
date: 2006-04-23
forum: General Help
---

### Post by medya on 2006-04-23
I get this error for apt-get ... (no matter what package)

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problem


I tried apt-get update
 
it didnt work

---

### Post by farruinn on 2006-04-23
When you ran apt-get update you had a reliable connection and didn't get any errors for that command?

---

### Post by medya on 2006-04-23
yes I do get error there too

> Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  403 Forbidden
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  403 Forbidden
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 4097 6EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976E AF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release: The following signatures were invalid: BADSIG 4097 6EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


---

### Post by medya on 2006-04-25
istill get that ugly error after each time i run apt-get . or run synaptic package maanger

---

### Post by Kevinator on 2006-04-25
Have you tried apt-get update again? It sounds like the repository was probably having problems, but it seems to be OK now. If it continues to break for you, you may need to use an alternate repository.

---

### Post by medya on 2006-04-25
how I can use an alternative repository?

---

### Post by farruinn on 2006-04-25
[quote=medya]how I can use an alternative repository?[/quote] 
Actually, your [http://koti.mbnet.fi]("http://koti.mbnet.fi/") is an alternative repository. I just tried apt-get update and there aren't any problems with the repositories right now. 

It looks like somehow the gpg keys used to authenticate the official repositories have been lost on your system (I don't know how this would happen). I think this should work for you: open System > Administration > Software Properties. Click the "Authentication" button, and in the new window click "Restore default keys".  After this you should be able to apt-get update without any problems.

---

### Post by medya on 2006-04-25
sorry but it didnt help look
> 
fred@ubuntu:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:7 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [47.6kB]
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://theli.free.fr](http://theli.free.fr) ./ Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [15.1kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [33.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  403 Forbidden
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  403 Forbidden
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Fetched 284kB in 3m54s (1209B/s)
[B]Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  403 Forbidden
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


---

### Post by medya on 2006-04-25
and when I run the Synpatic Package Manager
I get this error in the popup window :
**W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)**

---

### Post by Kevinator on 2006-04-30
koti.mbnet.fi does not seem to be a reliable repository, at least for you. You should try something else.

---

### Post by medya on 2006-04-30
[QUOTE=Kevinator]koti.mbnet.fi does not seem to be a reliable repository, at least for you. You should try something else.[/QUOTE]

how I can change it ?
are all those repositories the same ? (would it matter what I should change my resository to ?)

---

### Post by medya on 2006-04-30
how I can change my respo... ? 
I deleted that one in my respo's list , did I do a mistake ?

---

### Post by Banter on 2006-05-14
I have the very same problem:
> W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
meh. it'll get there.

---

### Post by twiistedkaos on 2006-05-14
I had the same problem after a new install to Ubuntu, I simply removed it from my repository.

```

Applications
...
Add Software
...Settings
..............Repositories

```
Then simple "delete" the one that is causing trouble.

---

### Post by Banter on 2006-05-14
I simply commented out the koti.mbnet.fi line in my sources.list

---

