---
title: "problem downloading repositories"
date: 2006-03-30
forum: General Help
---

### Post by yellow beard on 2006-03-30
ok, so when ever i try apt-get update, or to download a package i get awhole lot of this:

> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Tem porary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release). gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.g](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.g) pg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Tempor ary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Rele](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Rele) ase.gpg  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release) .gpg  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Pac kages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i 386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restrict ed Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restric ted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/ main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updat es_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/ restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary -updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/m ain Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security _main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/r estricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-se curity_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/u niverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-secu rity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_h oary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dis ts_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or dir ectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or dir ectory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.


so obviouslly it cant connect to the servers, would this be caused by being behind a proxy? any help would be great.

---

### Post by kcbanner on 2006-03-30
This may sound dumb but...can you browse the net? If so try pinging the us.archive.ubuntu.com and see waht happens :D

---

### Post by yellow beard on 2006-04-02
yes i can browse the net. i go to the [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) site no problem with firefox but if i try to download anything it doesnt work.

---

### Post by teasum on 2006-04-03
I seem to be having a similar problem with a recent server install (base system) I did on an old piece of hardware.  I can browse to the internet (via firefox) off a live CD, but through the base system I installed, I get an almost identical error from apt-get.  

One question: do you have the CD entry uncommented in /etc/apt/sources.list?  I ask because if that repository isn't loading (i.e. returning the same error), then it might help locate where the problem is, since it's a local resource.    

I'm asking people for help on this right now too....  I'll let you know if I hear anything!

---

### Post by tspec on 2006-04-03
i had this problem once before, i was able to fix it by doing "apt-get dist-upgrade", you could give that a shot if you haven't already.

---

### Post by teasum on 2006-04-03
[QUOTE=tspec]i had this problem once before, i was able to fix it by doing "apt-get dist-upgrade", you could give that a shot if you haven't already.[/QUOTE]

I can't speak for the originator of this post, but I tried "apt-get dist-upgrade" already.  I don't see how apt can upgrade without access to the repositories, however...

---

### Post by teasum on 2006-04-06
[QUOTE=yellow beard]yes i can browse the net. i go to the [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) site no problem with firefox but if i try to download anything it doesnt work.[/QUOTE]

Follow-up:

Yellow beard, did you find a solution for this issue?  Did you try configuring Synaptic and/or apt-get to use a proxy server (if you have one)?  Here's a post on this topic if you haven't tried it: [http://ubuntuforums.org/showthread.php?t=152500&highlight=Proxy+server+apt-get](http://ubuntuforums.org/showthread.php?t=152500&highlight=Proxy+server+apt-get)

---

### Post by yellow beard on 2006-04-07
*SOLVED*

I just had to add my proxy address top apt.conf and it worked like a charm.

---

