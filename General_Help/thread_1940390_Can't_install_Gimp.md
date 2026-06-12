---
title: "Can't install Gimp?"
date: 2012-03-13
forum: General Help
---

### Post by Spewed on 2012-03-13
Apparently nothing can simply "Come easy" on Ubuntu. So I try installing GIMP and here is what it says. I'll need a very noob friendly way to fix this. Anyone know anything? 

Thanks, once again.


The following packages have unmet dependencies:

gimp: Depends: python-gtk2 (>= 2.8.0) but 2.24.0-2 is to be installed
      Depends: libc6 (>= 2.11) but 2.13-20ubuntu5.1 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
      Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
      Depends: libgs9 (>= 8.61.dfsg.1) but 9.04~dfsg-0ubuntu11.5 is to be installed
      Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.6-0ubuntu5 is to be installed
      Depends: libgudev-1.0-0 (>= 147) but 1:173-0ubuntu4.2 is to be installed
      Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is to be installed
      Depends: librsvg2-2 (>= 2.14.4) but 2.34.1-2 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

---

### Post by AlexDudko on 2012-03-13
How are you trying to install it?

What's the full output of
> sudo apt-get install gimp

---

### Post by Perfect Storm on 2012-03-13
Also try do a;
```
sudo apt-get update && sudo apt-get upgrade
```
first.

---

### Post by AlexDudko on 2012-03-13
Here is the link which can help you [https://answers.launchpad.net/ubuntu/+source/apt/+question/189247](https://answers.launchpad.net/ubuntu/+source/apt/+question/189247)

---

### Post by Spewed on 2012-03-13
> **AlexDudko said:**
> How are you trying to install it?

What's the full output of

I have tried via the Terminal and the software center. But for good measure I tried doing what you suggested just incase I've missed something. Here are the results. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (>= 2.7.5) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.7.5-z) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Spewed on 2012-03-13
> **Artificial Intelligence said:**
> Also try do a;
```
sudo apt-get update && sudo apt-get upgrade
```first.

Didn't work either unfortunately.

---

### Post by mc4man on 2012-03-13
It appears you are using the gimp ppa,
If so see this thread, you will not be able to install normally atm, the libgimp package has an incorrect dependency
[http://ubuntuforums.org/showthread.php?p=11762338#post11762338](http://ubuntuforums.org/showthread.php?p=11762338#post11762338)

You could if desired build the ppa's source, correcting the /debian/control file or you could download all the needed packages, extract the problem libgimp2 package, edit it's control file, repackage it & then  install the lot of them thru dpkg

Otherwise wait for the ppa to fix it's package

---

