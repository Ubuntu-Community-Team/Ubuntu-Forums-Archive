---
title: "problems installing flash in mozilla"
date: 2006-02-25
forum: General Help
---

### Post by rkakkar on 2006-02-25
on "installing missing plugins", mozilla automatically downloads flash. after the download is complete, it states that it couldn't complete the installation and that i need to do it manually. any help?

i'm using firefox 1.5

---

### Post by andrewsawyer on 2006-02-25
Pretty sure there is a how-to on how to do this in the tips and tricks section.

---

### Post by rkakkar on 2006-02-25
I followed the steps in one of the HOWTOs, but it still hasn't worked. the plugin did not show when i typed

```

about:plugins

```

in the location bar. i've attached relevant screenshots.

---

### Post by jvnn on 2006-02-26
I'm in the same boat here.
Synaptic shows flashplayer-mozilla 7.0.25.0.0ubuntu1 is installed.
automatic install thru firefox 1.5 fails just like it di for rkakkar.
do I manual install, or use automatix or?

Thanks - Joel

---

### Post by aysiu on 2006-02-26
Enable the Multiverse repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

And then ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by rkakkar on 2006-02-26
[QUOTE=aysiu]Enable the Multiverse repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

And then ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```[/QUOTE]
apparently it didn't install. i straight away did 

$sudo apt-get install flashplugin-nonfree

since i had updated the repositories sometime earlier...but here was the output:

rahul@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libruby
Suggested packages:
  mozilla-browser mozilla-browser-snapshot mozilla-firefox
Recommended packages:
  libstdc++2.10-glibc2.2
The following NEW packages will be installed:
  flashplugin-nonfree libruby
0 upgraded, 2 newly installed, 0 to remove and 65 not upgraded.
Need to get 26.1kB of archives.
After unpacking 193kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe libruby 1.8.2-1 [3504B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse flashplugin-nonfree 7.0.25-5 [ 22.6kB]
Fetched 26.1kB in 7s (3421B/s)

Preconfiguring packages ...
Selecting previously deselected package libruby.
(Reading database ... 65621 files and directories currently installed.)
Unpacking libruby (from .../libruby_1.8.2-1_all.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.25-5_i386.deb) . ..
Setting up libruby (1.8.2-1) ...
Setting up flashplugin-nonfree (7.0.25-5) ...
Checking new upstream release...
I: checking [http://macromedia.rediris.es/tarball/debian/](http://macromedia.rediris.es/tarball/debian/)...
No new version is detected. ( = not installed)

rahul@ubuntu:~$

---

