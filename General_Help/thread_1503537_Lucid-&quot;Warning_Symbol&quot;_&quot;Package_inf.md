---
title: "Lucid-&quot;Warning Symbol&quot;: &quot;Package information is Outdated...&quot; Why?"
date: 2010-06-06
forum: General Help
---

### Post by emarkay on 2010-06-06
I have been constantly getting the red "Warning Symbol" that tells me that my "Update information is outdated..."  Of course I luse Update Manager and "Sudo Apt-get update/upgrade" in Terminal, but this appears after a bit, everytime I reboot.

Could this be related to the GetDeb archives being offline (If so, then someone needs to get this fixed; an offline repo is not worthy of a  "DANGER WARNING ATTENTION" symbol!

Could this also be related to this bug?
[http://ubuntuforums.org/showthread.php?p=9422634#post9422634](http://ubuntuforums.org/showthread.php?p=9422634#post9422634)

Regardless if this is a bug, what package is this related to?

---

### Post by emarkay on 2010-06-07
Can someone please confirm?

---

### Post by FuturePilot on 2010-06-07
If a repository is unavailable, it kind of breaks Apt in a way. Disable the Getdeb repos and it should fix it.

---

### Post by emarkay on 2010-06-08
> **FuturePilot said:**
> If a repository is unavailable, it kind of breaks Apt in a way. Disable the Getdeb repos and it should fix it.


Is this a reported bug?

---

### Post by zazootheparrot on 2010-08-13
Actually, I have the same problem. The warning sign appeared when I update the packages once and the sign is still there. I have restarted my computer several times but it won't disappear. Using the terminal to update the packages the following message appears:

```
GPG error : http://dl.google.com stable Release: The following signatures were invalid: NODATA 1 NODATA 2

```also, 
```
Failed to fetch 
http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 
returned an error code (2)

```and, 
```
Some index files failed to download,
 they have been ignored, or old ones used instead.

```Could you please tell what what the problem is?

Many thx

---

### Post by zazootheparrot on 2010-08-17
I have no idea what just happened but I can no longer see the warning sign. So package manager doesn't give any errors atm. :)

---

