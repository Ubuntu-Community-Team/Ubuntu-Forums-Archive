---
title: "I could not able to upgrade anything!!"
date: 2010-08-20
forum: General Help
---

### Post by saidbakr on 2010-08-20
Hi,
Currently, I run Gimp 2.6.8 on Ubuntu 10.04. There is new version of Gimp 2.6.10. I could not able to upgrade to the latest version. For example:
```

apt-get upgrade gimp

```

It does not give any result. I removed gimp from Ubuntu Software Center then I tried to install it from [GetDeb.net]("http://www.getdeb.net/software/GIMP"), also I have got the same old version 2.6.8. It seems like that Ubuntu does not download the new version, but it just use the old package of 2.6.8 that already downloaded before!

This problem may extends to other applications and package such as Kubuntu-desktop which I removed it using tasksel command in-order to reinstall it again to fix login loop problem for kdm. In this example, I choose complete remove from synaptic before installing it by tasksel .

I need to know how to really remove a package, or even how to push Ubuntu to re-download it again?

---

### Post by snowpine on 2010-08-20
First a clarification: Ubuntu is a "snapshot" distribution (not "rolling release"); this means GIMP 2.6.10 will never be officially supported for Ubuntu 10.04. It will probably be in the *next* Ubuntu release (10.10). So before proceeding, ask yourself, "Do I *really* need the new version, or can I stick with the current, stable, supported version?"

If you want to install the latest, at your own risk, the easiest way to do so is to download and build the source from [http://www.gimp.org/downloads/#mirrors](http://www.gimp.org/downloads/#mirrors)

If you've never compiled from source before, here is a tutorial: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I'm sure you've heard the phrase "open source software" before; this is exactly what it means! GIMP distributes their application as source code, which the different distros (like Ubuntu) can then test, build, and distribute to their users. Or, you can skip the middleman and get the source straight from GIMP--you can even modify it for your needs (if you know how)!

Good luck! :)

(edit) From the GIMP site:

> The source can be downloaded from ftp.gimp.org. Binary packages for various supported platforms should become available soon; please check the Downloads section. 

So if you wait a little while you might be able to install it from a .deb instead of source. :)

---

### Post by Frogs Hair on 2010-08-20
There is a ppa for Gimp 2.7.1  I found here in the Cafe.

sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn

sudo aptitude update

sudo aptitude upgrade 

sudo aptitude install gimp

---

