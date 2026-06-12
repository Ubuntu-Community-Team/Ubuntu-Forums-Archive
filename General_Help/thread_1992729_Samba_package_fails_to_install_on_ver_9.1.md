---
title: "Samba package fails to install on ver 9.1"
date: 2012-05-31
forum: General Help
---

### Post by HGM Engineering on 2012-05-31
Good afternoon all - 

Samba packages will not install on Ubuntu ver. 9.1  (I know, this is not the most recent release)

I have run the command:   sudo apt-get install smbfs
and the command:            sudo apt-get install smbfs --fix-missing

and I get the response:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  keyutils
The following NEW packages will be installed:
  smbfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,012kB of archives.
After this operation, 5,718kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  smbfs
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main smbfs 2:3.4.0-3ubuntu5.8
  404  Not Found [IP: 91.189.88.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main smbfs 2:3.4.0-3ubuntu5.8
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.4.0-3ubuntu5.8_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.4.0-3ubuntu5.8_amd64.deb)  404  Not Found [IP: 91.189.92.166 80]

Is there another location from which to download and install the samba package on release 9.1?    Any help is greatly appreciated.

Thank you in advance for any assistance

- HGM Engineering

---

### Post by redmk2 on 2012-05-31
> **HGM Engineering said:**
> ...

Is there another location from which to download and install the samba package on release 9.1?    Any help is greatly appreciated.

Thank you in advance for any assistance

- HGM Engineering

There are no up to date repos for Ubuntu 9.10.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty")

---

### Post by HGM Engineering on 2012-05-31
Thank You redmk2 for the quick response, I will see if I can get the Samba package for ver 9.10 from the link you sent.

It seems that Samba was never downloaded & set up when the Ubuntu OS was originally installed.

- HGM Engineering

---

