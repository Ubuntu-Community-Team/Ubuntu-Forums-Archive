---
title: "JDownloader in Ubuntu 11.10 Beta via PPA"
date: 2011-09-05
forum: General Help
---

### Post by JonM33 on 2011-09-05
I've been able to use this program in the past but can't seem to get it working via command line in 11.10. I followed the commands below...

```
sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader
```

I get the error below.

```
W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
```

I'm probably a 4 on a scale of 10 for using Linux. Not sure what I am doing wrong? Do I need to change something on my part?

---

### Post by FBML on 2011-09-05
there is no version for ubuntu 11.10 in repository yet .. ;D
try it manually from official website :
[http://jdownloader.org/download/index](http://jdownloader.org/download/index)

Try this :
$ wget [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)
$ chmod +x jd.sh
$ ./jd.sh

---

### Post by JonM33 on 2011-09-08
Okay, I tested it now and it works - they have updated it. Also had to install the JRE (Java Runtime Environment) via these commands first.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by /bee/ on 2011-11-09
```
bee@frich:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts[sudo] password for bee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Unable to locate package sun-java6-plugin
E: Package 'sun-java6-fonts' has no installation candidate
```

wait, what?

---

### Post by AngelX on 2011-11-11
Just do the following in a terminal window:

```

sudo add-apt-repository ppa:jd-team/jdownloader

sudo apt-get update

sudo apt-get install jdownloader
```

This installs jdownloader, now just find it in your apps and run it, it will update the 1st time is run so need to be patient.

enjoy!

---

### Post by biggmac419 on 2012-03-25
> **AngelX said:**
> Just do the following in a terminal window:

```

sudo add-apt-repository ppa:jd-team/jdownloader

sudo apt-get update

sudo apt-get install jdownloader
```This installs jdownloader, now just find it in your apps and run it, it will update the 1st time is run so need to be patient.

enjoy!
Thanks sir.

---

### Post by NonCorporeal on 2012-04-11
Thank you to FBML, worked!

---

