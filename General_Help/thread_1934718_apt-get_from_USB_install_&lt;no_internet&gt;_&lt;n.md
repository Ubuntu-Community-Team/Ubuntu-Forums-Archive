---
title: "apt-get from USB install &lt;no internet&gt; &lt;no CD drive&gt; Ubuntu 11.10"
date: 2012-03-02
forum: General Help
---

### Post by RHub787 on 2012-03-02
Hi, I installed Ubuntu 11.10 (Oneiric) from a bootable USB drive.(My PC has no CD drive)  The installation went smoothly. Ubuntu, however did not detect my wireless network card which has the T.I. ACX 100 chipset.

I found a thread here in the forums for "a patch to compile acx 100/111 driver in kernel 2.6.31"

This patch requires the build-essential package, unfortunately I cannot seem to get **apt-get** working to install build-essential. Ubuntu seems to be looking for the package in the installation CD.(Which I don't have)

These are the steps I've taken so far to attempt to fix this problem:

1. Log in as root

2. Created a directory named **repositories** in */home*

3. Copied **all** files from the bootable USB to */home/repositories*

4. Used the Software Sources application to add new repository
> deb file:///home/repositories oneiric main restricted 5. Open Terminal

6. apt-get update (i am already logged in as root but tried sudo apt-get update as well)
**Result:**

> root@rob-buntu:~# apt-get update
Ign file: oneiric InRelease
Get:1 file: oneiric Release.gpg [198 B]                                    
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
  
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Get:2 file: oneiric Release [1,765 B]
Reading package lists... Done 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/InRelease](http://archive.canonical.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch file:/home/repositories/dists/oneiric/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.7. apt-get install build-essential (also tried sudo)
**Result:**

> The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libtimedate-perl
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 852 kB of archives.
After this operation, 3,850 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main g++ i386 4:4.6.1-2ubuntu5
  Could not resolve 'archive.ubuntu.com'
Err file:/home/repositories/ oneiric/main g++ i386 4:4.6.1-2ubuntu5
  File not found
Err file:/home/repositories/ oneiric/main libtimedate-perl all 1.2000-1
  File not found
Err file:/home/repositories/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5
  File not found
Err file:/home/repositories/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5
  File not found
Err file:/home/repositories/ oneiric/main build-essential i386 11.5ubuntu1
  File not found
Err file:/home/repositories/ oneiric/main libalgorithm-diff-perl all 1.19.02-2
  File not found
Err file:/home/repositories/ oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1
  File not found
Err file:/home/repositories/ oneiric/main libalgorithm-merge-perl all 0.08-2
  File not found
Failed to fetch file:///home/repositories/pool/main/g/gcc-defaults/g++_4.6.1-2ubuntu5_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/libdpkg-perl_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/dpkg-dev_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/b/build-essential/build-essential_11.5ubuntu1_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-2_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-1build1_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
***The USB installation went smoothly and the .iso checksum matches up.
Any ideas are greatly appreciated. Thanks!

---

### Post by kurt18947 on 2012-03-02
Probably a stupid suggestion -- if so, sorry -- but is there any way to get a wired connection?  The likelihood of a ethernet connection working seems better than wireless.  The other thing I've done is keep an old, slow but seems very compatible wifi adapter.  It's been plug 'n' play for me on every distro since 9.04, I believe.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152&Tpk=trendnet%20tew-424ub](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152&Tpk=trendnet%20tew-424ub)

When I had a problem like yours I'd dig that out, plug it in and establish a connection, update and download any required software, get the newer faster adapter working then put 'ol blue back in the drawer until I needed it again.

---

### Post by RHub787 on 2012-03-02
Wow, that looks great!  

stupid question...  would i be able to *apt-get install build-essential* with just an internet connection and no CD.  This is my first Ubuntu installation.

(the wireless card im trying to install now is actually the same speed. haha.  This is a comp im building from discarded parts.  )  But for 10 bucks, cant go wrong!


**EDIT:** Thanks for the suggestion, but I am still would like to add the repositories manually.  I can access the internet via puppy Linux, which has kernel 2.6.33.2 and reads the card fine.

---

### Post by cortman on 2012-03-02
Ok, not the brightest idea perhaps, but you have the names of every .deb package you need right there:

```
g++_4.6.1-2ubuntu5_i386.deb
libtimedate-perl_1.2000-1_all.deb
libdpkg-perl_1.16.0.3ubuntu5_all.deb
dpkg-dev_1.16.0.3ubuntu5_all.deb
build-essential_11.5ubuntu1_i386.deb
libalgorithm-diff-perl_1.19.02-2_all.deb
libalgorithm-diff-xs-perl_0.04-1build1_i386.deb
libalgorithm-merge-perl_0.08-2_all.deb
```

Why not search for these in your copied CD files, move them into a folder of their own, then run

```
sudo dpkg -iR folder_name
```

---

### Post by RHub787 on 2012-03-03
Thanks for the help!  I got it working!

I looked at

> Failed to fetch file:///home/repositories/pool/main/g/gcc-defaults/g++_4.6.1-2ubuntu5_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/libdpkg-perl_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/dpkg-dev_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/b/build-essential/build-essential_11.5ubuntu1_i386.deb  File not found
Failed to fetch   file:///home/repositories/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-2_all.deb    File not found
Failed to fetch   file:///home/repositories/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-1build1_i386.deb    File not found
Failed to fetch   file:///home/repositories/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb    File not found                      and got all the .DEB packages from the online repos, and manually placed them in the right directories, and WALA!

sometimes the simplest ideas are the best.  And I clearly overlooked it.
Thanks again.

Now I have build-essential, but still cannot compile the acx 100 driver.  I think I start another post for that.

---

### Post by cortman on 2012-03-03
Great! Everyone needs a little "brain joggle" sometimes. :)

There are plenty of wireless wizards on this forum, so you should be set with help on your other problem.

Oh, and mark this thread as [SOLVED], if you would. Thanks, and good luck!

---

