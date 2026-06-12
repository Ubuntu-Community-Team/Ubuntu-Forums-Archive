---
title: "ubuntu ftp"
date: 2006-03-07
forum: General Help
---

### Post by sh33p on 2006-03-07
Anyone know of any good ftp clients for ubuntu? I tried gftp but it kept saying there was an error during installation ( I was using a .deb installer). Thanks.

---

### Post by IYY on 2006-03-07
Just get gFTP from the repos, using synaptic.

---

### Post by Xian on 2006-03-07
An error? What type was this....
Post the output from a terminal:

$ sudo apt-get install gftp

!! Make sure you enable the [extra repositories](https://wiki.ubuntu.com/AddingRepositoriesHowto) !!

---

### Post by aysiu on 2006-03-07
FileZilla under Wine. No kidding.

---

### Post by sh33p on 2006-03-07
Building dependency tree... Done
The following extra packages will be installed:
  gftp-text
The following NEW packages will be installed:
  gftp gftp-text
0 upgraded, 2 newly installed, 0 to remove and 69 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
sam@ubuntu:~$

---

### Post by aysiu on 2006-03-07
Sounds as if your sources.list is messed up or has conflicting repositories. This may help:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

---

### Post by sh33p on 2006-03-07
Just kept trying that command in terminal and it finally worked. Thanks everyone.

---

### Post by justinjstark on 2006-03-07
You could also set nautilus up to work with ftp.  It makes things really simple; you can just drag and drop your files to and from the remote ftp folder.

In gnome, just go to Places -> Connect to Server.  Select FTP (with login) from the dropdown and fill in the information and press ok.  Then you will have an FTP connection located in the Places menu that will open up a nautilus folder.

Alternatively, just enter an ftp location in the nautilus location bar like this
```
ftp://username@server.com
```

Myself: I use gftp at the moment.  The one in the repos works fine for me.

---

### Post by m0biu5 on 2006-03-07
Yeah, I use gFTP at the moment as well. I don't like it as much as some of the windows counterparts, but it does its job. =)

---

