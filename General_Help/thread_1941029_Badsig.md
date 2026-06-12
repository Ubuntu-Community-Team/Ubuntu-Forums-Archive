---
title: "Badsig"
date: 2012-03-14
forum: General Help
---

### Post by astrobob.tk on 2012-03-14
Hello,

I've been getting, for quite a long time, the following sort of Badsig messages (several of them) when updating.

I read several threads here & none helped. I also followed this: [http://blog.drewwithers.com/2009/12/how-to-fix-ubuntu-gpg-error-badsig.html](http://blog.drewwithers.com/2009/12/how-to-fix-ubuntu-gpg-error-badsig.html)

& what it did is change the errors to:

```
W: GPG error: http://debs.slavino.sk testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC3068F0E9C5D7EF
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/karmic/Packages.gz  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Help is greatly appreciated

---

### Post by astrobob.tk on 2012-03-14
Update: the GPG error was fixed with:
```

gpg --recv-keys
gpg --export EC3068F0E9C5D7EF | sudo apt-key add -

```

but what about the others?

---

### Post by cortman on 2012-03-14
You apparently have some repositories added that are going 404. If you know how, edit your /etc/apt/sources.list file and remove the offending repository entries. If that doesn't make sense, please post the output of

```
cat /etc/apt/sources.list
```

Thanks!

---

### Post by astrobob.tk on 2012-03-23
> **cortman said:**
> You apparently have some repositories added that are going 404. If you know how, edit your /etc/apt/sources.list file and remove the offending repository entries. If that doesn't make sense, please post the output of

```
cat /etc/apt/sources.list
```Thanks!

Thanks corman :)

I solved the remastersys error by following the new instructions here: [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

& the Natty errors by removing their entries.

Al that remains now is the Opera error which I'm searching for its solution.

Thanks again

---

