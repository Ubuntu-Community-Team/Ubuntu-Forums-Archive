---
title: "GPG Key Error"
date: 2011-04-19
forum: General Help
---

### Post by chwebb1 on 2011-04-19
Hello All,
I have not been able to update my computer for the last 10 days because of an Ubuntu GPG key error. When I try to update the package repository, I get: 
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 6D4535A284C5AD45 Launchpad Pep8Simulator
W: GPG error: http://us.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://packages.medibuntu.org maverick Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```I have tried doing:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```for each of the keys that is is unable to verify. Does anyone know how to fix this?
Thanks.

---

### Post by hwttdz on 2011-04-19
After doing the apt-key command (which fetches the key).  You need to tell the system that you trust it.  

gpg --armor --export KEYID | apt-key add -

see also: [http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/](http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/)

---

### Post by chwebb1 on 2011-04-19
Hello,
When I run
```
gpg --armor --export 16126D3A3E5C1192 | apt-key add -

```
I get:
```
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
```

Any idea what I'm doing wrong?
Thanks.

---

