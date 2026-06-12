---
title: "software center problem"
date: 2011-11-09
forum: General Help
---

### Post by TheDieSeL on 2011-11-09
I'm using 11.10 Ubuntu ... lately I'm facing a critical problem ..

when i open Ubuntu software center and click install on any application 

it gives my two dialogues :

1: Failed to download package files / Check your Internet connection.

2: Requires installation of untrusted packages / The action would require the installation of packages from not authenticated sources.


...

i opened Terminal run : sudo apt-get update     it gives me this :

> 
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 57C44545AC951808 Launchpad PPA for Francesco Mondello
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.


By the way i tried the Us main server as download server  .. it gives the same error .. 
then tried another one from US : [http://ftp.egr.msu.edu/pub/ubuntu/archive](http://ftp.egr.msu.edu/pub/ubuntu/archive)

it download some programs , but doesn't get ubuntu updates .. and i tried to get back to main server and US main server both gives the error mentioned up ...

i hope someone helps me troubleshoot this problem  because i'm in the process of full dependent on ubuntu linux and aborting windows OS for good ..

and i hope the solution to be explained simply because i'm not very familiar with ubuntu and linux OS

---

### Post by TheDieSeL on 2011-11-10
I hope some one helps me with this issue  ... or it is a common not solved yet problem ?

---

### Post by Enigmapond on 2011-11-10
Regarding the GPG errors, my solution in this link may help:
[http://ubuntuforums.org/showthread.php?t=1877141](http://ubuntuforums.org/showthread.php?t=1877141)

Regarding the errors from the Bisigi Launchpad account, this project is now dead so I would remove those from your source.list

Hope this helps.

---

### Post by Frogs Hair on 2011-11-10
The PPAS you are using don't appear to be compatible with 11.10 . I only found 11.04 packages . The Bisgi themes are only GTK 2 compatible  .

The themes creator states there will be no support for Gnome 3 . [http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)

---

### Post by TheDieSeL on 2011-11-10
@ Enigmapond   Thanks man  it helped me   i can now download software and updates (but still says in update manager  that last time i updated my system was 15 days ago and that's not true)

@ Frogs Hair  Thanks for your help but i Didn't get what you are saying  but i'm checking out the website you provided in your reply ..

---

