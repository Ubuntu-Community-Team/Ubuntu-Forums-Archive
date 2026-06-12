---
title: "Three Problems that gets me frustrated."
date: 2010-01-06
forum: General Help
---

### Post by Inhumanity on 2010-01-06
Hi guys, I'm getting so frustrated here and I don't know how to fix these problems.

**First. **

[IMG]http://img268.imageshack.us/img268/5590/errorup.png[/IMG]

I keep getting this error when i try to install the libwebkit-dev update.

**Second.**

Why does everytime I log back in to my Gnome Desktop, My panel items(Clock, Indicator Applet, Brightness, Volume) are messed up, so i have to move them one-by-one to their default places.


**Third.**

I noticed my boot time has began to slow down(30-40seconds).



Thank you guys.\\:D/

---

### Post by Inhumanity on 2010-01-06
Bumpy Bump

---

### Post by blueridgedog on 2010-01-06
Is this a wubi install?

---

### Post by 3rdalbum on 2010-01-06
The 'webkit update' appears to be from an external repository. Try disabling this repository.

---

### Post by Inhumanity on 2010-01-06
Nope. It isn't wubi

---

### Post by Inhumanity on 2010-01-06
> **3rdalbum said:**
> The 'webkit update' appears to be from an external repository. Try disabling this repository.

Uhm, Sorry bro, I'm quite new with this. How do I know what repository to remove for this webkit update?

---

### Post by switch10 on 2010-01-06
Right click on the stuff that is moving around, and check "lock to panel".

---

### Post by Inhumanity on 2010-01-06
> **switch10 said:**
> Right click on the stuff that is moving around, and check "lock to panel".

:KS Wow thanks, i didn't know there's a lock option. I'm an idiot lol. thanks.


Two Problems Remaining.

---

### Post by 3rdalbum on 2010-01-06
> **Inhumanity said:**
> Uhm, Sorry bro, I'm quite new with this. How do I know what repository to remove for this webkit update?

Apparently it's the one with "webkit-team" in the URL.

---

### Post by Inhumanity on 2010-01-06
> **3rdalbum said:**
> Apparently it's the one with "webkit-team" in the URL.

Got it. thanks bud, I have disabled it.



But i got a new problem :(

[IMG]http://img27.imageshack.us/img27/5262/error2wf.png[/IMG]

I got this problem. How to solve this?

---

### Post by switch10 on 2010-01-06
Hey man,

Run

```
sudo apt-get update
```
 
and post the errors...

---

### Post by Inhumanity on 2010-01-06
> **switch10 said:**
> Hey man,

Run

```
sudo apt-get update
```
 
and post the errors...

here

```
Err http://archive.ubuntu.mnosi.org karmic/main Packages                       
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/restricted Packages                 
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/restricted Sources                  
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/main Sources                        
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/universe Sources
  403  Forbidden
Fetched 74.9kB in 15s (4,850B/s)
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/universe/source/Sources.gz  403  Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by switch10 on 2010-01-06
> **Inhumanity said:**
> here

```
Err http://archive.ubuntu.mnosi.org karmic/main Packages                       
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/restricted Packages                 
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/restricted Sources                  
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/main Sources                        
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-updates/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-backports/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/universe Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-security/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/restricted Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/main Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/multiverse Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/universe Packages
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/restricted Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/main Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/multiverse Sources
  403  Forbidden
Err http://archive.ubuntu.mnosi.org karmic-proposed/universe Sources
  403  Forbidden
Fetched 74.9kB in 15s (4,850B/s)
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/universe/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/restricted/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/main/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/multiverse/source/Sources.gz  403  Forbidden

W: Failed to fetch http://archive.ubuntu.mnosi.org/ubuntu/dists/karmic-proposed/universe/source/Sources.gz  403  Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
```



Here ya go...

[http://ubuntuforums.org/showthread.php?t=186455](http://ubuntuforums.org/showthread.php?t=186455)

...and that GPG error can be fixed by running:

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

---

### Post by Inhumanity on 2010-01-06
> **switch10 said:**
> Here ya go...

[http://ubuntuforums.org/showthread.php?t=186455](http://ubuntuforums.org/showthread.php?t=186455)

...and that GPG error can be fixed by running:

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

Thanks again bud. :popcorn:

---

