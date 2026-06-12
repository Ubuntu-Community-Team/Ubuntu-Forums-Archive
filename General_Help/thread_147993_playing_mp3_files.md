---
title: "playing mp3 files"
date: 2006-03-21
forum: General Help
---

### Post by macm10 on 2006-03-21
hello everytime i try to play an mp3 file it says that its not a audio stream and cannot play. i have tryed to play it in rythmbox. i have tryed downloading other players but allways get  random error messages when i try to install. please help

---

### Post by bonzodog on 2006-03-21
You need to install the mp3 codecs. Make sure your 'universe' and 'multiverse' repository is enabled in your /etc/apt/sources.list. Then, in the terminal, run apt-get update. Then open synaptic and search for mp3. There are some codecs that need to be installed, but I am unable to remember the filenames at present. You will also need to install extra codecs to run Win32 format files, as it is illegal for Ubuntu to distribute these with the install.

---

### Post by macm10 on 2006-03-21
ok first thing, how to do update the repository?

---

### Post by macm10 on 2006-03-21
when i download the repostiorys it gets stuck at file 5. then under the list it shows failed. umm what do i do now ?

edit:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed out

---

### Post by macm10 on 2006-03-21
another message:
The following problems were found on your system:
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by macm10 on 2006-03-21
please disregard all problems, i typed the proxy server in wrong

ok now what to download? so many things so many posibilities

---

### Post by jrib on 2006-03-21
the gstreamer0.8-mad package in universe will let you play mp3's

---

### Post by Trance Gemini on 2006-03-21
For addind mp3 support check out [here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29")

If you having troubles with repositories, check the guide [here]("https://wiki.ubuntu.com/SourcesList?highlight=%28sources%29") or [better here]("http://www.ubuntuguide.org/#extrarepositories") how to add extra ones

A few days ago I found a link here to a website, which can generate a sources.list file - search for it if my links weren't helpful :)

---

