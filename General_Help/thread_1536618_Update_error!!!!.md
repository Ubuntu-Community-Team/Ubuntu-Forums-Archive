---
title: "Update error!!!!"
date: 2010-07-22
forum: General Help
---

### Post by hemajith on 2010-07-22
I'm using Lucid and I have this following issue. I have all the updates installed via automatic update. I have the following error popping up periodically and every time I start my laptop,

"Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check"."

When I click on "run this action now" option, the update files is downloading but when the installation is running, I get this error,

"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead."

Can someone help me to rectify this problem?

---

### Post by quixote on 2010-07-24
The whole key nonsense ought to be a one-click update option.  However, for now we're stuck with the command line.  Also, firewalls can be an issue.  If you have one on your router, disable it briefly while sending the command to get the key.  Likewise if you use one on your computer.  

Open a terminal (Applications > Accessories > Terminal) and run:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 A8A515F046D7E7CF
```To make things easier, you can use ctrl-c to copy that line from here, and ctrl-**shift**-v to paste it into the terminal.

That should deal with it.

---

