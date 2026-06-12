---
title: "Aptitude thinks Karmic when really Lucid"
date: 2012-01-13
forum: General Help
---

### Post by northcide on 2012-01-13
Ubuntu server 10.04.3. Trying to do aptitude update and it shows karmic errors for some reason.  I have no idea why the update process complains of karmic repos. This is  causing problems installing some other packages since it thinks some of  them are missing.  Anyone have any ideas?

Thanks

[SIZE=1]> root@web-11:/usr/src/curl# aptitude update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
  404  Not Found [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
  404  Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
  404  Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.167 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
  404  Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
  404  Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
  404  Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
  404  Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
  404  Not Found [IP: 91.189.88.31 80]
Reading package lists... Done[/SIZE]

The contents of /etc/apt/sources.list is:
[SIZE=1]> 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe         
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
[/SIZE]

---

### Post by cortman on 2012-01-13
What are the contents of 

```
/var/lib/apt
```

?

If there are any files with Karmic in the name, delete them.

---

### Post by oldos2er on 2012-01-13
Are there any files in /etc/apt/sources.list.d/ ?

---

### Post by northcide on 2012-01-17
Sorry for the late response as i was out of town.

So /var/lib/apt did have a karmic file in it strangely.  I removed it and the update process succeeds now.

Something might still be messed up as the initial reason for me going in here was to get php5-curl installed (sorry i know i should probably start a new thread).

php5-curl does not show installed via dpkg --get-selections. when i run aptitude install php5-curl i receive:

web-11:~# aptitude install php5-curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for php5-curl
No candidate version found for php5-curl
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

I dont understand how that could be.

Thanks again for all the replies.

---

### Post by cortman on 2012-01-17
> **northcide said:**
> Sorry for the late response as i was out of town.

So /var/lib/apt did have a karmic file in it strangely.  I removed it and the update process succeeds now.

Something might still be messed up as the initial reason for me going in here was to get php5-curl installed (sorry i know i should probably start a new thread).

php5-curl does not show installed via dpkg --get-selections. when i run aptitude install php5-curl i receive:

web-11:~# aptitude install php5-curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for php5-curl
No candidate version found for php5-curl
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

I dont understand how that could be.

Thanks again for all the replies.

Hm...

```
sudo apt-get purge php5-curl
sudo apt-get install php5-curl
```

Sometimes the dumb answers just work...

---

### Post by northcide on 2012-01-20
Cortman, thanks but unfortunately I've already tried that without any luck :/

I think it has something to do with the fact that this machine was forced to run php5.2, instead of the current 5.3.x.  not sure how it's being forced into staying with 5.2 however.

---

### Post by cortman on 2012-01-20
How about

```

sudo apt-get purge php5-curl
sudo apt-get install -f
```

It'll remove php5 from your system, then check for and resolve any dependency errors, which hopefully should result in a downloading of the correct php5 package.

---

