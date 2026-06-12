---
title: "Trouble installing updates"
date: 2010-03-20
forum: General Help
---

### Post by bhakeman on 2010-03-20
Lately, when I try installing updates or installing from synaptic, I get the following error message

E: tff-mscorefonts-installer:subprocess installed post-installation script returned error exit status 1

The errors started when I tried installing programs to view DVD's.  But the error pops up for just about anything I try to install.  Any thoughts?

Thanks

(Ubuntu 9.10 on an HP Compaq ne8240)

---

### Post by zvacet on 2010-03-20
In terminal type 

```
sudo dpkg --configure -a
```

and see if it helps.If not type

```
sudo apt-get update && sudo apt-get upgrade
```

and post output here to see errors if any.

---

### Post by tommynz1975 on 2010-03-20
it seems to be an international issue maybe??
I wonder if their is massive strain on the servers.

their is a thread

[http://ubuntuforums.org/showthread.php?t=1434073](http://ubuntuforums.org/showthread.php?t=1434073)

I will try that configure option..

---

### Post by tommynz1975 on 2010-03-20
Thank you 

I tried the dpkg --configure -a and it fixed what ever upset things.

could some one briefly explain why it fixed the errors, such as

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bhakeman on 2010-03-20
Tried sudo dpkg --configure -a, and got the following:

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
 

I then entered sudo apt-get update && sudo apt-get upgrade, and got the following:

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bhakeman on 2010-03-25
Any thoughts, or should I try re-installing 9.10?  Or try an older release?

---

### Post by snowpine on 2010-03-25
> **bhakeman said:**
> I then entered sudo apt-get update && sudo apt-get upgrade, and got the following:

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

This part is easy to fix. :) System->Administration->Software Sources, then uncheck the box for the Ubuntu CD-ROM.

---

### Post by bhakeman on 2010-03-25
> **snowpine said:**
> This part is easy to fix. :) System->Administration->Software Sources, then uncheck the box for the Ubuntu CD-ROM.

Thanks, I'll have to give it a try.  Now I wish I hadn't left my laptop at home today.

---

