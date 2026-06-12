---
title: "Failed to download repository information - Check your internet connection"
date: 2012-02-08
forum: General Help
---

### Post by rviswana on 2012-02-08
When I try to update the repository information in synaptic update manager.. it fails with the following information

"Failed to download repository Information - Please Check Your Internet Connection".. 

My Internet connection is very much alive and kicking.. what could be the problem....?  This has been happening for a few weeks now.. my repository information is over 58 days old..

I am running Ubuntu 11.10..

Please help..


Details of the error as under.. 

W:GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F9946354E9CFF4E, W:Failed to fetch [http://repository.spotify.com/dists/stable/non-free/source/Sources](http://repository.spotify.com/dists/stable/non-free/source/Sources)  404  Not Found
, W:Failed to fetch [ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric/Release](ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric/Release)  Unable to find expected entry 'IBM/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-updates/Release](ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-updates/Release)  Unable to find expected entry 'IBM/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-security/Release](ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-security/Release)  Unable to find expected entry 'IBM/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-proposed/Release](ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-proposed/Release)  Unable to find expected entry 'IBM/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-backports/Release](ftp://ftp.iitb.ac.in/distributions/ubuntu/archives/dists/oneiric-backports/Release)  Unable to find expected entry 'IBM/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Henkdroid on 2012-02-08
Try going to 'System Settings' then 'Software Sources' then deleting the repositories that are giving errors. Then try adding them back.

---

### Post by winh8r on 2012-02-08
Try what Henkdroid suggests above. Then if it is no different , try using a different mirror.

Also noticed that you are using ftp mirror, are you doing this for a reason? or is it just the default when setting up Ubuntu in India locale?

I would try not to use ftp mirrors for updates if possible, as I have often had problems with ftp being reliable in the past.

Hope this helps you.

---

