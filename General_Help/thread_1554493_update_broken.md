---
title: "update broken"
date: 2010-08-16
forum: General Help
---

### Post by mschira on 2010-08-16
Hi Guys 
I have a problem with the automatic updates. I have this problem for a while now (32 day...), I have been ignoring it because the error message sounded to me like it's got nothing to do with my system but with the ubuntu update servers. So I assumed they will fix it and I should not interfere and nag with stupid questions. Thing is - it doesn't.
when I use the update manager a lot of updates get downloaded but not installed. (I can see the list of updates expanding every time).
I get the following error message:

mschira@Humboldt:/home/$ sudo apt-get update
[sudo] password for mschira: 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg  
.....
.....cut for briefness
.....
Fetched 380B in 5s (70B/s)                            
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Failed to fetch [http://archive.canonical.com/dists/lucid/Release](http://archive.canonical.com/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

