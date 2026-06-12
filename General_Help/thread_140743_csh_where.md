---
title: "csh? where?"
date: 2006-03-06
forum: General Help
---

### Post by Death on 2006-03-06
Cant seem to install this as directed.

admin@server:~$ sudo apt-get install csh
Password: ***
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package csh


admin@server:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tcsh

I'm trying to setup mu Brother printer but I dont want to go beyond this step for all I do might go sour if this is wrong.
Thanks.

---

### Post by taurus on 2006-03-06
Perhaps you need to comment out all the lines in /etc/apt/sources.list that have universe and multiverse...  Then run "sudo apt-get update" before you try to install csh/tcsh again with apt-get!  However, it's strange that you don't already have both csh & tcsh on your machine when you install Ubuntu!  Did you by any change choose "server" when you installed it???

---

### Post by engla on 2006-03-06
tcsh is in the main repository! tcsh should be available without trouble...

Have you installed software with apt-get before? It could be that you don't have any "package repositories" enabled.

First, try to run "sudo apt-get update" and see if that fixes the problem (try install tcsh again), 
otherwise, you will have to edit your repositories...
There are many ways to do that, I prefer to use synaptic.

Open synaptic, 'gksudo synaptic' or the menu System > Administration > Synaptic package manager
Open the menu Settings > Repositories
You should have one called "Ubuntu 5.10 Breezy Badger" there. If not, click the add button and select Breezy from the dropdown, check at least "officially supported" and "restricted copyright" and save the changes. Hit reload and search for tcsh.

---

### Post by Death on 2006-03-06
The Repository seems fine. Updates has an issue.

> admin@server:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Fetched 1B in 6m0s (0B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by engla on 2006-03-08
I haven't tried the us. mirrors, but there seems to be some connection trouble with them.

```
http://**us**.archive.ubuntu.com
```

You can try removing the **us.** part in each of the repository urls, or replace it with some other country close to you (I don't know if there are any other mirrors close in North America though)

---

