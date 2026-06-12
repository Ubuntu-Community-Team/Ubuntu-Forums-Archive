---
title: "Problems with retreving packages"
date: 2012-01-15
forum: General Help
---

### Post by EmptySun on 2012-01-15
I'm having some problems with getting a few updates for 10.04 LTS.  Though I'm relatively new to working with Ubuntu, I can say I've learned a tad bit.

When doing the 'sudo apt-get update' there are a few problems. 
Here is what it gives me.
```
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg
Ign [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release.gpg
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic Release.gpg                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic/partner Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports/restricted Translation-en_US
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic Release                      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports Release
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid Release                           
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/main Packages                
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic/partner Packages             
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/restricted Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/universe Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/main Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/restricted Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/universe Sources
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic/partner Sources              
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") lucid/main Packages                     
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/multiverse Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/main Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/restricted Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/universe Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/main Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/restricted Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/universe Sources
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/multiverse Sources
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/main Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/restricted Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/universe Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/multiverse Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/main Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/restricted Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/universe Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-backports/multiverse Sources
  404  Not Found [IP: 91.189.92.180 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.180 80]

E: Some index files failed to download, they have been ignored, or old ones used instead. 

```I checked with Ubuntu Software Center, when I uncheck and recheck one of the sources, it causes an update of the cache, when I do so it only gets 95% and tells me,
"Failed to download repository information
Check your Internet connection."
Under details it gives quite a few URLs, here are the ones listed.

[> ]("http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.lzma")[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.gz)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.lzma)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.lzma)

I hope I can get this resolved.
[]("http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.lzma")

---

### Post by oldos2er on 2012-01-15
Karmic is end-of-life, its repositories are offline. You shouldn't be using Karmic repos anyway if you're running Lucid, so remove any Karmic repos from your sources.list.

---

### Post by bluexrider on 2012-01-15
Remove all the sources files directing to Karmic. That should resolve the issue.

---

