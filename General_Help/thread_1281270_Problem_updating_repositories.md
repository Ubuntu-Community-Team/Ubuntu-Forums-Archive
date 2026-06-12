---
title: "Problem updating repositories"
date: 2009-10-03
forum: General Help
---

### Post by Dirich on 2009-10-03
Hi, I've been getting the following error for a couple of days now. When I start Update Manager it says:



Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Problem parsing dependency Depends, E:Error occurred while processing libxcb-damage0 (NewVersion1),
E: Problem with MergeList /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages,
E: The package lists or status file could not be parsed or opened.'


EDIT:
I tried 
sudo apt-get --purge remove it.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
but I got the same error


I tried doing a sudo apt-get update, but I got exactly the same lines. Needless to say I found nothing when I did a search with google, so I'm kind of out of idea on how to solve this thing. Anyone with more experience than me that can help me out?

Thanks.

---

### Post by ermeyers on 2009-10-03
Try apt-get clean, then apt-get update.

---

### Post by arrange on 2009-10-03
Remove the offending file and run an update```

sudo mv /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages_corrupted
sudo apt-get update
```

---

### Post by Dirich on 2009-10-03
apt-get clean didn't solve the problem.

then I run a dpkg-reconfigure and blew my system before being able to try the other suggestion. I'll most likely need to reinstall everything since it doesn't even accept keyboard or mouse inputs on the login screen.

Thanks anyway.

---

### Post by arrange on 2009-10-03
*dpkg-reconfigure* what? This could be easily recoverable.

---

### Post by akakingess on 2009-10-03
Could this have to do with the fact that the main server is updating all of the mirrors worldwide with 9.10 and is supposed to either be slow or almost unavailable right now? Just a suggestion...

---

### Post by Willy Gatti on 2009-11-26
I started having the same exact problem with updating repositories in Karmic after uninstalling Opera.  I tried everything already mentioned in this post (apt-get clean, apt-get update, and removing offending files), but I still can't update my reposititories.  How do I fix the repositiories, so I can update them again?

---

### Post by dcstar on 2009-11-27
> **Willy Gatti said:**
> I started having the same exact problem with updating repositories in Karmic after uninstalling Opera.  I tried everything already mentioned in this post (apt-get clean, apt-get update, and removing offending files), but I still can't update my reposititories.  How do I fix the repositiories, so I can update them again?

Unless you post the exact error messages, you will get no help.

---

### Post by Willy Gatti on 2009-11-27
The error message I received was:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cybercookie72 on 2009-12-09
Greetings 


I was having same malformed error and I replaced my sources.list with::

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted


and that cleared things up for me...this is for 9.10 only

I also found a website that makes a sources.list from a form

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

it has a drop down for older ver of ubuntu

dont forget the run the commands for keys 
if there are any needed :popcorn:

---

