---
title: "Downloading from repositories is not working properly"
date: 2012-10-06
forum: General Help
---

### Post by mamboze on 2012-10-06
I'm having trouble downloading software from the repositories. 

Running "sudo apt-get --fix-missing update" from the terminal in an attempt to fix the problem gave the following:

> 
roy@medea:~$ sudo apt-get --fix-missing update
.......
W: Failed to fetch [http://ppa.launchpad.net/clubuntu/scribus-thai/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/clubuntu/scribus-thai/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/clubuntu/scribus-thai/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/clubuntu/scribus-thai/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/dists/oneiric/main/source/Sources](http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/dists/oneiric/main/source/Sources)  404  Not Found [IP: 133.24.255.161 80]
.............

W: Failed to fetch [http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/dists/oneiric-security/multiverse/binary-i386/Packages](http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/dists/oneiric-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 133.24.255.161 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.



[http://ftp.yz.yamagata-u.ac.jp](http://ftp.yz.yamagata-u.ac.jp) seems not to be responding or is it some local problem?

Any suggestions please

---

### Post by oldos2er on 2012-10-06
The clubuntu/scribus PPA only has software for one release, maverick. I would remove that PPA.

Same type of problem with [http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/dists/oneiric-security/multiverse/binary-i386/Packages](http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/archives/dists/oneiric-security/multiverse/binary-i386/Packages). [http://ftp.yz.yamagata-u.ac.jp/pub/linux/](http://ftp.yz.yamagata-u.ac.jp/pub/linux/) exists, but there is no ubuntu folder there.

You can remove these repositories with ```
gksu software-properties-gtk
```

---

### Post by mamboze on 2012-10-06
@oldos2er

Many thanks, it worked

---

### Post by oldos2er on 2012-10-06
You're welcome.

---

