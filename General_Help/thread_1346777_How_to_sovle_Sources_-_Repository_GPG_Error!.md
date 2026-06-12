---
title: "How to sovle Sources - Repository GPG Error!"
date: 2009-12-05
forum: General Help
---

### Post by beetlejuice321 on 2009-12-05
Recently I have been running into several GPG Errors when attempting to download new software or update my sources (apt-get update).  Some examples of errors I have received are below.

> W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org


Here is the solution I used from [Luigi]("http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/") which helped me greatly. This is the only solution that worked for me and its simple.  Hope it helps you.


> sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

---

### Post by bhongong on 2010-01-25
Hi, 

I still get the following errors:

Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

This problem started just about 3 days ago.

---

