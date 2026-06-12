---
title: "Cannot Update or Open Software Center (Internal Error)"
date: 2012-08-06
forum: General Help
---

### Post by ConfusedToHell on 2012-08-06
A couple days ago I received an error telling me that I could not update my Ubuntu software. I am currently running 12.04 Precise. It said something about not being able to access some server where it gets it's updates. So I decided to try doing a "sudo apt-get update" to see if that could solve the problem or give me more information. It was doing well for awhile then it gave me this about halfway through updating the ppa's:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 508A982D7A617FF4 Launchpad official ppa for pcsx2 team

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 133EAF26736E4F0B Launchpad PPA for falktx

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 5A9A06AEF9CB8DB0 Launchpad PPA for Ubuntu Wine Team

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release](http://archive.canonical.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

I've no clue what this means other than it cannot access the update archive, if there is a fix for this it would be nice since I can't seem to access the software center to even download new software and I also can't use the "sudo apt-get install" command either it seems. I want to say this is an urgent problem, but Ubuntu hasn't crashed yet.

---

### Post by cortman on 2012-08-06
Hi, run

```
sudo rm -r /var/lib/apt/lists
sudo apt-get update
```


And post back the results in [CODE] tags- the little hash # mark in the editing toolbar.

---

