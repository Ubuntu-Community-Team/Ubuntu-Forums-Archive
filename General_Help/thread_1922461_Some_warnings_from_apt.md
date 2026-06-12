---
title: "Some warnings from apt"
date: 2012-02-08
forum: General Help
---

### Post by Rafterman414 on 2012-02-08
So when I try to run
```
sudo apt-get update
```I am presented with an error message stating the following:

```
W: Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  File not found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```After receiving this error I attempted to do:

```
sudo apt-build update-repository
```And received the following:

```
Encountered a section with no Package: header
Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages
The package lists or status file could not be parsed or opened.
Can't call method "packages" on an undefined value at /usr/bin/apt-build line 70.

```I tried to do a search on some of this but did not find any information. Any thought on what could be causing this and how to fix it? I had just recently built some .deb packages from source using checkinstall and am wondering if that may have something to do with the issue.

EDIT: I get the following error also when trying to install packages as well.
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```EDIT: More new information: After doing some research I tried to remove the files in /var/lib/apt/lists and then reload the lists however I still get the previous error messages. I guess due to the limitations now imposed on me because of this I should categorize them as errors and not warnings.

---

### Post by Rafterman414 on 2012-02-08
Solved the problem. The issue was related to me building my own packages. In the software sources section there was an entry for:
```
file:/var/cache/apt-build/repository
```What I am guessing happened is this got added as a result of me building those packages. If anyone has any additional light they can shed on the situation it would be more then welcome.

---

### Post by mungatsuma on 2012-05-30
> W:Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  File not found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I still get that error, what did you do to resolve it. Also compiled and installed deb packages with checkinstall.

---

### Post by ewf on 2013-02-22
I had the same problem and it went away when I added a "main" directory to /var/cache/apt-build/

---

### Post by wildmanne39 on 2013-02-22
Old thread closed.

---

