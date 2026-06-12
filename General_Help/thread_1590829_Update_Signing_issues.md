---
title: "Update Signing issues"
date: 2010-10-08
forum: General Help
---

### Post by LeifAndersen on 2010-10-08
This started a few weeks ago, and has not stopped since.  Every time I try to check for updates, I get this:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://linux.dropbox.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://dl.google.com stable Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.getdeb.net lucid-getdeb Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release  

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release  

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/lucid/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Failed to fetch http://ppa.launchpad.net/flozz/flozz/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ppa.launchpad.net/testdrive/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

However, when I didn't check manually it worked just fine.  However, recently, the updates themselves also stopped working.  (And yes, they did seem to be signed when I got the updates).  So, I'm assuming that this means that somehow my PPA keys got screwed up somehow.  Is there any easy way I can fix it, or is it better for me just to install a new version of ubuntu.  (If so, I'll probably wait a week or so for the new one to come out).

Thank you for your help.

---

### Post by sikander3786 on 2010-10-08
First of all try changing the Update Server from System > Administration > Software Sources. Select Main Server preferably and reload. Is it solved? Post back any error messages encountered.

---

### Post by LeifAndersen on 2010-10-08
Thank you, but it didn't work.
```


W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D2BF771175034BEC
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B73EEC804D1BAE55
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

```

---

### Post by sikander3786 on 2010-10-08
Try this.

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

### Post by LeifAndersen on 2010-10-08
It worked, thank you.

---

