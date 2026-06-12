---
title: "Errors when updating Ubuntu"
date: 2012-04-27
forum: General Help
---

### Post by DobsonM on 2012-04-27
I was using the latest beta of Ubuntu which I installed 3 days ago, with the recent release I am now getting this error in the terminal when running "sudo apt-get update"

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://nz.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://nz.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/precise-updates/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have purged my PPA's but I get the same errors, what do I need to do?  I don't really want to have to do a clean install.

---

### Post by Rubi1200 on 2012-04-28
Hi,
try the following commands:

```
sudo apt-get clean
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
```

Run them one at a time and post error messages if relevant.

Also post the output of this:
```
cat /etc/apt/sources.list
```

---

