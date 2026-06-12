---
title: "W: Failed to fetch any help over here"
date: 2010-08-04
forum: General Help
---

### Post by rashidragon on 2010-08-04
hello all i am super new to ubuntu and i am using ubuntu serer 64bit and trying to make my own server i made allot of stuff by now but i am getting this error 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)
when updating using (sudo apt-get update)

```
Hit http://security.ubuntu.com lucid-security Release.gpg
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:1 http://us.archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Hit http://security.ubuntu.com lucid-security/restricted Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Sources
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid Release
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Err http://us.archive.ubuntu.com lucid-updates Release

Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Fetched 189B in 4s (42B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

help me ):P

---

### Post by dcstar on 2010-08-05
> **rashidragon said:**
> hello all i am super new to ubuntu and i am using ubuntu serer 64bit and trying to make my own server i made allot of stuff by now but i am getting this error 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)
when updating using (sudo apt-get update)
........

Do not use the default servers, select a different repository that is not overloaded as the main servers usually are.

---

