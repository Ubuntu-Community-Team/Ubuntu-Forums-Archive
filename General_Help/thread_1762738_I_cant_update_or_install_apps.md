---
title: "I cant update or install apps"
date: 2011-05-19
forum: General Help
---

### Post by earthsdestiny on 2011-05-19
I am having a problem that I cant update or install apps. I am using Natty under ubuntu classic and have tried these two posted fixes but they wont work

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update && sudo apt-get upgradeCheers,

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

these didnt work, i am kinda new to ubuntu and dont know where to start to look in order to fix this myself this is what I get when I run package manager and apt-get update. please help

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by StrayEddy on 2011-05-19
> **earthsdestiny said:**
> sudo apt-get update && sudo apt-get upgrade**Cheers,**
 
Yep that can t work.

---

### Post by earthsdestiny on 2011-05-19
98% [35 Translation-en bzip2 0 B] [Connecting to us.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US         
98% [36 Translation-en_US lzma 0 B] [Waiting for headers]/usr/bin/lzma: Decoder error
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Fetched 701 kB in 2min 17s (5,118 B/s)                                         
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

These are the errors and their location exactily when i run apt-get update, does this mean that the problem isnt on my system but in the update server?

---

### Post by plucky on 2011-05-19
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multivers e_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


The package name is incorrect.Checkout the space in the word multiverse.
 **multivers e_i18n**

That is probably caused by the spelling of the file on the server.Try changing your download server under **Software Sources**.

Good Luck

---

