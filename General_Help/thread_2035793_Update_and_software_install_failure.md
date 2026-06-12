---
title: "Update and software install failure"
date: 2012-07-31
forum: General Help
---

### Post by jktjs on 2012-07-31
I've been running kubuntu 12.04 for a few months now on a Samsung Chronos 7 laptop. It has recently (3-5 weeks?) become impossible to install updates or new software using muon package manager or update manager.

All attempts end with the error message:
The following errors occurred while applying changes:
Error: subprocess installed post-installation script returned error exit status 127

Similar problems occur with apt-get or aptitude on the command line.

sudo apt-get update returns 
[various package lines]
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: Unknown error executing gpgv
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: Unknown error executing gpgv

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release: Unknown error executing gpgv
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: Unknown error executing gpgv
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.


Attempts to install a package, such as:
suod apt-get install supertux

returns the error message
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6gpg: undefined symbol: UP
: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anyone any ideas about how to fix this?

Thanks.

---

### Post by raja.genupula on 2012-07-31
open your terminal and type this

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

if any error occurs let us know and if not then try again with your process .

---

### Post by jktjs on 2012-07-31
Thanks for the idea. I tried it but still get similar results:

sudo apt-get update:

....
Get:109 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en [14 B]
Get:110 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en [17.5 kB]
Fetched 25.1 MB in 7s (3,464 kB/s)                                                                          
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release: Unknown error executing gpgv
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release: Unknown error executing gpgv
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: Unknown error executing gpgv


And trying to install a random package:

[jkt@tench:~]$ sudo apt-get install supertux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
supertux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 413 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up apt (0.8.16~exp12ubuntu10.2) ...
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by raja.genupula on 2012-07-31
[http://askubuntu.com/questions/110118/gpg-error-while-updating](http://askubuntu.com/questions/110118/gpg-error-while-updating)

---

### Post by jktjs on 2012-08-01
Thanks for the link to the other bug report. I solved this with the following commands:

sudo mv /usr/local/lib/libreadline.so.6.2 /usr/local/lib/libreadline.so.6.2.old
sudo ln -s /lib/x86_64-linux-gnu/libreadline.so.6.2 /usr/local/lib/libreadline.so.6.2

Problem appears to be fixed and software is now updated.

---

