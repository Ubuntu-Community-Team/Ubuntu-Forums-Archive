---
title: "Upgrading help."
date: 2011-06-23
forum: General Help
---

### Post by dannyb2100 on 2011-06-23
I'm attempting to install some web applications which require me to update PHP amoung other things on our server, but I'm unable to upgrade my native Ubuntu OS, but am unable to for the following reasons.
I've never used Ubuntu, I've always used CentOS.
So any help on this new venture would be great,

root@:~# sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  update-manager-core: Depends: python-apt (>= 0.7.4ubuntu5) but it is not going to be installed
E: Broken packages
root@:~# sudo apt-get install python
Reading package lists... Done
Building dependency tree
Reading state information... Done
python is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@:~#

Thanks guys.:guitar:

---

### Post by snowpine on 2011-06-23
Welcome to the forums!

Try this to fix your broken package:

```
sudo apt-get -f install
```

Also a good idea to bring your system up-to-date:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

And to read the upgrade notes and release notes:
[www.ubuntu.com/download/ubuntu/upgrade](www.ubuntu.com/download/ubuntu/upgrade)
[www.ubuntu.com/getubuntu/releasenotes](www.ubuntu.com/getubuntu/releasenotes)

Post back with any error messages/problems and I'll try to help! :)

---

### Post by dannyb2100 on 2011-06-23
> **snowpine said:**
> Welcome to the forums!

Try this to fix your broken package:

```
sudo apt-get -f install
```Also a good idea to bring your system up-to-date:

```
sudo apt-get update
sudo apt-get dist-upgrade
```And to read the upgrade notes and release notes:
[www.ubuntu.com/download/ubuntu/upgrade]("http://www.ubuntu.com/download/ubuntu/upgrade")
[www.ubuntu.com/getubuntu/releasenotes]("http://www.ubuntu.com/getubuntu/releasenotes")

Post back with any error messages/problems and I'll try to help! :)

Hey there, thank you so much for the quick reply.

First, on ficking the broken packages, this is the result.
root@:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@:~#

```
root@:~# sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


root@:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by dFlyer on 2011-06-23
I don't think 8.10 is still supported.

---

### Post by snowpine on 2011-06-23
Support for 8.10 ended April 2010. You'll have to follow the End of Life Upgrade Guide:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Another possibility is to do a fresh reinstall of a supported release (10.04 is the current Long Term Support).

---

### Post by dannyb2100 on 2011-06-23
> **snowpine said:**
> Support for 8.10 ended April 2010. You'll have to follow the End of Life Upgrade Guide:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Another possibility is to do a fresh reinstall of a supported release (10.04 is the current Long Term Support).

Thank you so much, I will start this first thing in the morning once I'm back in the office.
But for now, it's 4:30 am here in England and I need to get some sleep :)

---

### Post by dFlyer on 2011-06-23
You might want to download the latest LST version 10.04 for server support.

---

### Post by dannyb2100 on 2011-06-23
> **dFlyer said:**
> You might want to download the latest LST version 10.04 for server support.

From what I read, I need to go 8.10 to 9.10 and upgrade from there, it seems like a rather long winded process, but with the LST, I believe I wont have to do it for a while.
Will keep you guys updated with how I progress.:lolflag:

---

### Post by dannyb2100 on 2011-06-24
Update!
root@:~# sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server.
Everything was going so well up to this point, any ideas?

---

### Post by dFlyer on 2011-06-24
I'm not sure but I don't think that is possible with an out of date (EOL) version. The correct path would be 8.10 > 9.04 > 9.10 > 10.04

---

