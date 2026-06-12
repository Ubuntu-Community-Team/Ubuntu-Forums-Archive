---
title: "extra repositories problem"
date: 2006-02-07
forum: General Help
---

### Post by eXTerminate on 2006-02-07
hi. i'm looking for help with eenabling extra repositories in kubuntu 5.10 breezy.
i followed the steps shown in easylinux.info/wiki/Ubuntu . the problem is that i can't get the packadges i want, i get 

W: Couldn't stat source package list [http://packages.freecontrib.org]("http://packages.freecontrib.org") breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org]("http://packages.freecontrib.org") breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

and when i do > 
sudo apt-get update 
i get :

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz]("http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz")  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz]("http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz")  404 Not Found

ideas? 
thanks in advance.
--

---

### Post by Jucato on 2006-02-07
could you kindly post your /etc/apt/sources.list for us to check?

---

### Post by eXTerminate on 2006-02-07
here it is:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

but as i said - i used what's listed in the unofficial guide

---

### Post by gingermark on 2006-02-07
The PLF doesn't support AMD64 packages as far as I know (at least that's what it says [here](http://wiki.ubuntu-fr.org/doc/plf)). I'm not sure what to suggest. If you are indeed looking for 64 bit packages, maybe post what you are after? I don't know much about the AMD64 architecture.

---

### Post by eXTerminate on 2006-02-07
well. i can't install multimedia codecs (most of them). can't watch videos. 
plus i seem to miss some other things like the message i get when i try to install the new firefix, or eclipse, or..<long list>..:

error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

do you know where i can get libgtk-x11...blahblah....?

---

### Post by gingermark on 2006-02-07
[QUOTE=eXTerminate]well. i can't install multimedia codecs (most of them). can't watch videos. 
plus i seem to miss some other things like the message i get when i try to install the new firefix, or eclipse, or..<long list>..:

error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

do you know where i can get libgtk-x11...blahblah....?[/QUOTE]
I think there are a few issues here, and I'm probably not the person to deal with them but anyways...

Can you confirm with version of Breezy you are using? Your initial error message made me think you're using the AMD64 as opposed to the x86 version. Is this correct?

Getting hold of the new version of Firefox is something you should search the forums for - there is a method to do it, but due to some dependency issues you can't just upgrade the version that comes with Breezy.

If you are using the AMD64 version, I'm afraid I can't help you further. You should be able to compile the stuff you need if there are no binary packages available, apart from the proprietery multimedia codecs and the other proprietery programs that are only available as binary packages in the first place.

---

### Post by eXTerminate on 2006-02-07
[QUOTE=gingermark]I think there are a few issues here, and I'm probably not the person to deal with them but anyways...

Can you confirm with version of Breezy you are using? Your initial error message made me think you're using the AMD64 as opposed to the x86 version. Is this correct?

Getting hold of the new version of Firefox is something you should search the forums for - there is a method to do it, but due to some dependency issues you can't just upgrade the version that comes with Breezy.

If you are using the AMD64 version, I'm afraid I can't help you further. You should be able to compile the stuff you need if there are no binary packages available, apart from the proprietery multimedia codecs and the other proprietery programs that are only available as binary packages in the first place.[/QUOTE]

yes i have an amd 64 version of breezy. about compiling those packets myself - hmmmm. i'm VERY new to linux so... i'll look for some documentation.
right now i'm being bitchslapped by gcc. i installed it (at least i think so), but it doesn't compile my hello world program... 

this is a little offtopic but... i get this error when i try to compile hello.cpp :

proba.cpp:5: error: ‘cout’ was not declared in this scope

that would mean that i didn't install everything, right?
-----

---

### Post by gingermark on 2006-02-07
There are threads all over the place explaining how to compile packages - one is [here](http://ubuntuforums.org/showthread.php?t=118208). There are probably better ones though.

My advice would be to post in the [Kubuntu AMD64 forum](http://www.ubuntuforums.org/forumdisplay.php?f=110) and hopefully someone more knowlegable on these issues can help.

As I understand it there aren't currently as many repositories supporting AMD64, so one (rather extreme) solution might be to install the x86 version. If you stick your /home directory on a separate partition, you could then install the AMD64 version when the situation improves. I've actually just bought a new AMD Athlon 64 cpu as part of an upgrade I'm about to undertake, and that is what I plan on doing.

But otherwise, the AMD64 forums are probably your best bet. Again, I apologise for not being able to help you further. Good luck.

---

### Post by eXTerminate on 2006-02-07
thank you for your good will.

---

