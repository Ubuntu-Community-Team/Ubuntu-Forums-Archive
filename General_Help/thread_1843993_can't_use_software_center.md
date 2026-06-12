---
title: "can't use software center"
date: 2011-09-14
forum: General Help
---

### Post by linuxjones on 2011-09-14
I recently installed ubuntu 11.04 and am trying to use the software center.  Currently there are no "install" buttons to click on.  I am behind a proxy, but those settings are correct system wide.  I can access the internet fine.  Another forum suggested running sudo apt-get update, but doing so gives the following message.  Any help is appreciated.


```
root@jones:~# sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Get:1 http://us.archive.ubuntu.com natty InRelease                             
Get:2 http://extras.ubuntu.com natty InRelease                                 
Get:3 http://archive.canonical.com natty InRelease                             
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Get:4 http://us.archive.ubuntu.com natty-updates InRelease
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Err http://extras.ubuntu.com natty/main Sources                                
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com natty/main i386 Packages                          
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com natty/main Translation-en_US                      
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com natty/main Translation-en
  Unable to connect to extras.ubuntu.com:http:
Ign http://archive.canonical.com natty InRelease  
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:5 http://us.archive.ubuntu.com natty-security InRelease                    
Err http://archive.canonical.com natty/partner Sources                         
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com natty/partner i386 Packages                   
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com natty/partner Translation-en_US               
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com natty/partner Translation-en                  
  Unable to connect to archive.canonical.com:http:
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com natty-security InRelease                      
Get:6 http://us.archive.ubuntu.com natty/main i386 Packages
96% [6 Packages bzip2 0 B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:7 http://us.archive.ubuntu.com natty/multiverse i386 Packages
97% [7 Packages bzip2 0 B] [Connecting to us.archive.ubuntu.com (91.189.88.40)]bzip2: (stdin) is not a bzip2 file.
Get:8 http://us.archive.ubuntu.com natty/restricted i386 Packages              
97% [8 Packages bzip2 0 B] [Connecting to us.archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex
Err http://us.archive.ubuntu.com natty/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-updates/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com natty-security/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]
Fetched 1,221 B in 2min 0s (10 B/s)
W: GPG error: http://us.archive.ubuntu.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://extras.ubuntu.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://archive.canonical.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://us.archive.ubuntu.com natty-updates InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://us.archive.ubuntu.com natty-security InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/binary-i386/Packages  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/i18n/Translation-en_US  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/i18n/Translation-en  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_US  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.46 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Rubi1200 on 2011-09-14
Hi and welcome to the forums :)

I suggest changing from your current server to the Main Server and see if that resolves the problem.

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]

You can access this either via Synaptic or the Software Center.

---

