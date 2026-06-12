---
title: "Centralized Patch Managment for Ubuntu 10"
date: 2010-08-09
forum: General Help
---

### Post by CPL2010 on 2010-08-09
I just moved my household over to Ubuntu 10 this weekend, the 4 kids are happy with it and the wife is happy with it.  I've been happy with it since 7.x.  So basically no more XP in the house, now I need to upgrade my infrastructure.  I was thinking mediabuntu as the kids collect a tonne of crap online and it would serve as a file/print server.  Plus it would act as the patch distribution point.

What is the equivalent to WSUS/SMS/SCCM in the Ubuntu universe and is there a good book or a How To somewhere to get it setup.  Or even a process that is accepted as standard.  Just something that bugged me while installing five boxes this weekend was the amount of internet chatter 5 PC's can do over the course of an evening to retreive security updates.

Thanks in advance.:D

---

### Post by FuturePilot on 2010-08-09
The closest thing is probably [apt-cacher-ng]("http://www.unix-ag.uni-kl.de/~bloch/acng/")

---

### Post by bodhi.zazen on 2010-08-09
Moved to general help

---

### Post by Logan1985 on 2010-08-09
Perhaps puppet?

Not sure if it's suitable for your situation though...

[http://www.puppetlabs.com/puppet/introduction/](http://www.puppetlabs.com/puppet/introduction/)

---

### Post by earthpigg on 2010-08-09
hi,

you are able to set up file sharing and stuff, right?

prior to installing, updates get downloaded to /var/cache/apt/archives

the trick, then, is to have other computers on the LAN look first at the server's /var/cache/apt/archives before looking at the remote repositories.

there are many ways to go about it.

the first method popping into my head is to have the ubuntu 10.04 workstations mount the 10.04 server's var/cache/apt/archives locally at /var/cache/apt/archives with read/write access, and then do the upgrade.

if the server already downloaded the update, then the workstation will install it from there. if not, it will download it from ubuntu's repos to the server's /var/cache/apt/archives and install it.


we may have a friendly graphical tool to do that, but i don't know what it is called. 

i came across [this]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/"). i suspect that sysadmins of large workstation linux deployments have their own little collection of scripts to automate all of this.

anything you find yourself typing over and over again can be compressed into a shell script.

have you played with ssh and sshfs yet?

---

### Post by CPL2010 on 2010-08-09
That's it reading through the white papers.  patch management and systems management.  It's a little over kill for what I want it to do but as an infrastructure guy, it'll be interesting to see how this develops.

---

### Post by CPL2010 on 2010-08-09
> **earthpigg said:**
> hi,

you are able to set up file sharing and stuff, right?

prior to installing, updates get downloaded to /var/cache/apt/archives

the trick, then, is to have other computers on the LAN look first at the server's /var/cache/apt/archives before looking at the remote repositories.

there are many ways to go about it.

the first method popping into my head is to have the ubuntu 10.04 workstations mount the 10.04 server's var/cache/apt/archives locally at /var/cache/apt/archives with read/write access, and then do the upgrade.

if the server already downloaded the update, then the workstation will install it from there. if not, it will download it from ubuntu's repos to the server's /var/cache/apt/archives and install it.


we may have a friendly graphical tool to do that, but i don't know what it is called. 

i came across [this]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/"). i suspect that sysadmins of large workstation linux deployments have their own little collection of scripts to automate all of this.

anything you find yourself typing over and over again can be compressed into a shell script.

have you played with ssh and sshfs yet?
Actually that reminds me of how HPUX manages centralized patch distribution and OS deployments.  Mapping the workstations back to the var directory.  Going to start digging up my old notes for HPUX and see if it translates well.  If I can figure it out I'll write up a How To and post it up.

---

### Post by earthpigg on 2010-08-09
[this]("http://www.ubuntu.com/cloud/private/deploy") looks promising.

some combination of the words "Local Repository Ubuntu LAN", i think, would also be appropriate to google search for.

---

### Post by CPL2010 on 2010-08-09
> **earthpigg said:**
> hi,

you are able to set up file sharing and stuff, right?

prior to installing, updates get downloaded to /var/cache/apt/archives

the trick, then, is to have other computers on the LAN look first at the server's /var/cache/apt/archives before looking at the remote repositories.

there are many ways to go about it.

the first method popping into my head is to have the ubuntu 10.04 workstations mount the 10.04 server's var/cache/apt/archives locally at /var/cache/apt/archives with read/write access, and then do the upgrade.

if the server already downloaded the update, then the workstation will install it from there. if not, it will download it from ubuntu's repos to the server's /var/cache/apt/archives and install it.


we may have a friendly graphical tool to do that, but i don't know what it is called. 

i came across [this]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/"). i suspect that sysadmins of large workstation linux deployments have their own little collection of scripts to automate all of this.

anything you find yourself typing over and over again can be compressed into a shell script.

have you played with ssh and sshfs yet?
The guy in Africa with the bandwidth has the plan I'm going to kick around this weekend.  The goal is zero Windows in the house by monday.  Then focus on building my daughter a bed frame.

Thanks guys!

---

