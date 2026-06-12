---
title: "How to install opera?"
date: 2011-10-15
forum: General Help
---

### Post by piyush| on 2011-10-15
I have Ubuntu 11.10 BETA
I have not yet updated it to 11.10 official build and ATI graphics driver too (I'll be doing these things as soon as possible)

I am not able to install opera .deb package
when I try, the Ubuntu Software Center gives "Internal Error"

when I try to install it via terminal through these commands
```

 sudo dpkg -i opera_11.51.1087_amd64.deb

```this error comes
```

dpkg: error: dpkg status database is locked by another process

```SO should I first install the drivers and updates?
or there is something else ?

---

### Post by Frogs Hair on 2011-10-15
I used the instructions at the link because neither the software center nor  the Gdebi package installer would open the Opera .deb . I have seen this before and it was resolved in a matter of days.

If you manage to get Opera installed you may get an error from the update manager until this is resolved . I simply removed the source from software sources post installation . I will reinstall when the package error is resolved . [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by gandaran on 2011-10-15
> dpkg: error: dpkg status database is locked by another process
you have to close ubuntu software center or synaptic to install from command line 
gdebi is the best application to install .deb packages, install gdebi from software center

---

### Post by piyush| on 2011-10-16
> **gandaran said:**
> you have to close ubuntu software center or synaptic to install from command line 
gdebi is the best application to install .deb packages, install gdebi from software center
Even GDebi is giving me the error
"It is either corrupted or you dont have the permission to open the file"

It is not corrupted because I have tried various versions of opera to install , all giving me same error
and I am the only user, so permission error doesn't fit here

---

### Post by piyush| on 2011-10-16
ok just figured it out
sudo dpkg -i opera.deb
successfully installed
thanks for the help guys :)

---

### Post by AmpersUK on 2011-10-16
> **piyush| said:**
> ok just figured it out
sudo dpkg -i opera.deb
successfully installed
thanks for the help guys :)

For Novices, if the opera file is in your Downloads folder, and the name of your file is as downloaded, add the extras. For example, mine was in the download file and I used the 64-bit version so used:

~/Downloads/opera_11.51.1087_amd64(1).deb

Thanks for this though, I have now managed to get it working.

---

### Post by ruario on 2011-10-18
The problems are related to issues with Software Center and Gdebi not being able to install lzma compressed deb files, unless lzma is available. dpkg can handle it because it uses xz to open lzma.

More info here:
[http://my.opera.com/community/forums/findpost.pl?id=10564932](http://my.opera.com/community/forums/findpost.pl?id=10564932)

Here are copies of Opera repckaged with bzip2 compression so that you can more easily install them:
[32-Bit Opera 11.51 for Ubuntu 11.10 (Oneiric Ocelot)](http://people.opera.com/ruario/opera-11.51-for-ubuntu-11.10-oneiric-ocelot/opera_11.51.1087_i386.deb)
[64-Bit Opera 11.51 for Ubuntu 11.10 (Oneiric Ocelot)](http://people.opera.com/ruario/opera-11.51-for-ubuntu-11.10-oneiric-ocelot/opera_11.51.1087_amd64.deb)

P.S. Here is the main bug if you want to track it:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188)

---

### Post by ruario on 2011-10-19
Ok, Opera 11.52 is released. It uses bzip2 compression for now to work around the issue and also includes a fix for a recent security issue:

[ftp://ftp.opera.com/pub/opera/linux/1152/](ftp://ftp.opera.com/pub/opera/linux/1152/)

---

