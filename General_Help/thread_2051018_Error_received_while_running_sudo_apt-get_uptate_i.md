---
title: "Error received while running sudo apt-get uptate in terminal"
date: 2012-09-01
forum: General Help
---

### Post by jlapinski4 on 2012-09-01
Reading package lists... Error!
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This all happened spontaneously and not while I was doing anything. 

Any help would be appreciated!

Thanks!

---

### Post by hansdown on 2012-09-01
Hi jlapinski4.

Could you please tell us if you were attempting to download, and install a particular app?

Thanks.

---

### Post by jlapinski4 on 2012-09-01
No, I wasn't doing anything in fact my laptop was on and I wasn't even working on it. An error message popped up and asked me to submit an error report against the update manager.

I have tried updating using both the terminal and update manager, with the update manager I get the following:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by jlapinski4 on 2012-09-01
I resolved my problem using the following commands

sudo rm /var/lib/apt/lists/* -rf
followed by 

sudo apt-get update

Thanks for your response!

---

