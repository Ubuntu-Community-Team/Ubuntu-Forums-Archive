---
title: "gzip:/var/lib/apt/lists/partial/archive.canonical.com..... Hash Sum Mismatch"
date: 2012-01-07
forum: General Help
---

### Post by rakesh.swapna on 2012-01-07
Update manager troubles me like this.... (Ubuntu 11.10, 32 bit)

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

---

### Post by plucky on 2012-01-07
> W: Failed to fetch [http://ppa.launchpad.net/ferramrober...source/Sources](http://ppa.launchpad.net/ferramrober...source/Sources) 404 Not Found


See [Here](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/) 
There is no PPA Repository for oneiric,so you should disable it in your Software Sources.

> W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner _binary-i386_Packages Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_on eiric_main_binary-i386_Packages Hash Sum mismatch

Remove the files with ```
sudo rm -R /var/lib/apt/lists/partial/*
``` then run ```
sudo apt-get update && sudo apt-get upgrade
``` and see if it fixes the problem.If you still get the "Hash Sum mismatch",try a different server.

Good Luck

---

### Post by rakesh.swapna on 2012-01-07
Thank you, Its worked for me. Both solved and another major problem also solved. 

My Update Manager was saying my system is not updated for last 23 days even though I was able to install all updates. That also solved and now indicates your system is up to date!!!!

Thanks again

---

### Post by TheKojuEffect on 2012-06-07
I had the same problem.
Changed the Download Server from Update Manager -> Ubuntu Software -> Download from ...

And then
apt-get update
and
again reverted back to the previous Download Center.

Worked for me...

---

### Post by tbriggs707 on 2013-05-13
I'm completly new to Ubuntu and I don't know how to change the download server, can you explain how you did that because I tried running the commands 

sudo rm -R /var/lib/apt/lists/partial/*

and

sudo apt-get update && sudo apt-get upgrade

but that didn't work for me.

---

### Post by oldos2er on 2013-05-13
tbriggs707, you're much more likely to get help if you start a new thread in the Absolute Beginners forum. Give as many details as possible, including which version of Ubuntu you're using.

---

