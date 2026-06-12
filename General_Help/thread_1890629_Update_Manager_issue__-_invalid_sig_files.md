---
title: "Update Manager issue  - invalid sig files"
date: 2011-12-03
forum: General Help
---

### Post by lonewolf88 on 2011-12-03
(Apologies if already covered here, did a quick search and failed to find this one.)

Lubuntu 11.10, 3.0.0-14-generic-pae (i686)

Update Manager is showing that I have not run updates for last 44 days, 
which is not correct.  I regularly run same and have been receiving updates.

Not a whiz at Linux, but ran sudo apt-get update in a terminal, and came 
back with a lot of invalid sig errors, and failure to fetch HTTP sources.

"Reading package lists... Done
W: A error occurred during the signature verification. The repository is not 
updated and the previous index files will be used. GPG error: 
[http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic 
Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease: The following 
signatures couldn't be verified because the public key is not available: 
NO_PUBKEY 2EBC26B60C5A2783
W: A error occurred during the signature verification. The repository is not 
updated and the previous index files will be used. GPG error: 
[http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were 
invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key 
<ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic 
Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG DF8030F05ED1D082 Launchpad PPA for Claws 
Mail
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG 7B1AB59047B4D1C4 Launchpad qbittorrent
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG 34C08E07CF3D9164 Launchpad PPA for 
Alessandro Lanave
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic 
Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG 53D9CF3EE3B3D1B9 Launchpad PPA for PhobosK
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG D2B5F4E7C3BB95BB Launchpad Gstyle PPA
W: A error occurred during the signature verification. The repository is not 
updated and the previous index files will be used. GPG error: 
[http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: The following signatures were 
invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key 
<ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic 
Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following 
signatures were invalid: BADSIG DFB844B8BB91632D Launchpad PPA for Weather 
Indicator Team
W: A error occurred during the signature verification. The repository is not 
updated and the previous index files will be used. GPG error: 
[http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic 
Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not 
updated and the previous index files will be used. GPG error: 
[http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release: The following signatures 
were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 
<ftpmaster@ubuntu.com>

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-](http://au.archive.ubuntu.com/ubuntu/dists/natty-)
backports/Release  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release](http://extras.ubuntu.com/ubuntu/dists/natty/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-](http://archive.ubuntu.com/ubuntu/dists/oneiric-)
backports/Release  

W: Failed to fetch 
[http://ppa.launchpad.net/lxde/ppa/ubuntu/dists/oneiric/main/binary-](http://ppa.launchpad.net/lxde/ppa/ubuntu/dists/oneiric/main/binary-)
i386/Packages  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-](http://archive.ubuntu.com/ubuntu/dists/oneiric-)
proposed/Release  

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-](http://ppa.launchpad.net/mozillateam/thunderbird-)
stable/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch 
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-)
i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones 
used instead"

Looks like a mess, how to fix?

As usual, thanks in advance!

---

### Post by raja.genupula on 2011-12-03
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <keys>

and for remaining problems ,open your source list in /etc drive with sudo gedit and then place # at problem link sources

---

### Post by lonewolf88 on 2011-12-03
> **raja.genupula said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <keys>

and for remaining problems ,open your source list in /etc drive with sudo gedit and then place # at problem link sources

Thanks Raja, running first command above I get following error:

bash: syntax error near unexpected token `newline'

Err, should I be putting something in "<keys>"?

---

### Post by elliotn on 2011-12-03
> **lonewolf88 said:**
> Thanks Raja, running first command above I get following error:

bash: syntax error near unexpected token `newline'

Err, should I be putting something in "<keys>"?

in <keys> put the key displayed in the error. put it without the <>

---

### Post by lonewolf88 on 2011-12-03
> **elliotn said:**
> in <keys> put the key displayed in the error. put it without the <>

Thanks, thought I was missing something here.

Can you define exactly what a "key" should be that goes here?

For instance, what part of this error message should be used?

"W: A error occurred during the signature verification. The repository is not 
updated and the previous index files will be used. GPG error: 
[http://au.archive.ubuntu.com]("http://au.archive.ubuntu.com/") natty-backports Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic 
Signing Key <ftpmaster@ubuntu.com>"

Apologies for my technical incompetence!

(And is there anyway to run this command with multiple "keys", or do they have to be done one by one?)

---

### Post by raja.genupula on 2011-12-04
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **40976EAF437D05B5**

key means that bold one you can find code similar to that in the errors of your update manager...

---

### Post by lonewolf88 on 2011-12-04
> **raja.genupula said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **40976EAF437D05B5**

key means that bold one you can find code similar to that in the errors of your update manager...

Thanks once again!

Is this message anything to be concerned about?  :-

"gpg: no ultimately trusted keys found"

---

### Post by raja.genupula on 2011-12-04
[http://doc.norang.ca/apt-key-verification-problems.html](http://doc.norang.ca/apt-key-verification-problems.html)

---

### Post by lonewolf88 on 2011-12-04
> **raja.genupula said:**
> [http://doc.norang.ca/apt-key-verification-problems.html](http://doc.norang.ca/apt-key-verification-problems.html)

Thanks once again!

---

### Post by dvandok on 2011-12-06
> **raja.genupula said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **40976EAF437D05B5**

key means that bold one you can find code similar to that in the errors of your update manager...

 The messages actually reads BADSIG, indicating an invalid signature rather than a missing key.  Could there be a bug in the gpg code for apt-get?

This is definitely a bug in apt. See [http://askubuntu.com/questions/64721/reloading-the-package-manager-gives-a-gpg-error](http://askubuntu.com/questions/64721/reloading-the-package-manager-gives-a-gpg-error). The fix is to remove /var/lib/apt/lists and then mkdir -p /var/lib/apt/lists/partial to get apt unwedged.

---

