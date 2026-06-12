---
title: "Could not download all repository indexes?"
date: 2009-08-12
forum: General Help
---

### Post by gksudo on 2009-08-12
Hello, I just installed Ubuntu 8.04.(After 8.10 bricked on me) I went to the Add/Remove to download some codecs and other programs. However, When I had to reload all the package information It gave me two errors. In two different windows.
#1 Problem
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

#2 Problem
An error occurred(no i was not running multiple synaptic package managers.)
The following details are provided:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

So I went to the software sources under administration an allowed the Third-Party software, yada yada yada.(google was no help surprisingly.)
Any help would be great,

---

### Post by rajeev1204 on 2009-08-12
1.Check internet connection

2.Try a different server from software sources (system>admin>softwrae sources)

3.Restart PC and try again.

---

### Post by gksudo on 2009-08-12
Thanks, that worked. I changed my source to mirrors.us.kernel.org/ubuntu

---

