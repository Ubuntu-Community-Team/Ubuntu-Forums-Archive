---
title: "synaptic problems"
date: 2006-05-08
forum: General Help
---

### Post by theaffman on 2006-05-08
hi thank you all for your kind help.

 When i try to use synaptic or apt-get i get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I run that command, and it hangs on the following:

bryan@ubuntu:~$ sudo dpkg --configure -a
Password:
dpkg: dependency problems prevent configuration of python-kde3:
python-kde3 depends on python2.4-kde3; however:
Package python2.4-kde3 is not installed.
dpkg: error processing python-kde3 (--configure):
dependency problems - leaving unconfigured
Setting up debtags (1.4+svn20050912-0ubuntu1) ...
Get:1 [http://people.debian.org/~enrico/tags/tags-current.gz](http://people.debian.org/~enrico/tags/tags-current.gz) [215kB]
Get:2 [http://people.debian.org/~enrico/tags/vocabulary.gz](http://people.debian.org/~enrico/tags/vocabulary.gz) [14.5kB]
Fetched 230kB in 8s (26.3kB/s)
Reading tag data and vocabulary for [http://people.debian.org/~enrico/tags/](http://people.debian.org/~enrico/tags/)...
Writing system vocabulary...
Writing merged tag database...


after trying this a few times, i can't update or install anything.

---

### Post by Sef on 2006-05-08
> dpkg: dependency problems prevent configuration of python-kde3:
python-kde3 depends on python2.4-kde3; however:
Package python2.4-kde3 is not installed.

Try this to get it working:

From the Terminal (or Konsole, if Kubutnu)

sudo (or kdesu) apt-get update (if you can't get that to work, just go to the next step)

sudo (or Kdesu) apt-get install python2.4-kde3

---

### Post by theaffman on 2006-05-08
Thank you Sef, but that didn't work.

Here is the contents of the terminal after following your ideas:

bryan@ubuntu:~$ sudo apt-get update
Password:
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:2 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release [110B]
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release [2327B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:4 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages [10.6kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Get:5 [http://kubuntu.org](http://kubuntu.org) breezy/main Packages [88.2kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Get:6 [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages [743B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Get:10 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages [1100B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:11 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg [65B]
Get:12 [http://theli.free.fr](http://theli.free.fr) ./ Packages [960B]
Get:13 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:14 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release [702B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Get:15 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [58.9kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:18 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages [3485B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:19 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources [1728B]
Get:20 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [16.9kB]
Get:26 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35.0kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:30 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [232kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:34 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages [545B]
Get:35 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages [2337B]
Get:36 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources [316B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [915kB]
Get:39 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources [473B]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [585kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Fetched 4578kB in 6m3s (12.6kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
bryan@ubuntu:~$ sudo apt-get install python2.4-kde3
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
bryan@ubuntu:~$ 

as you can see we go in circles.

---

