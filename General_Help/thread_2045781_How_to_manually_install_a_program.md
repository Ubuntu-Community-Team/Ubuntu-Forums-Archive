---
title: "How to manually install a program?"
date: 2012-08-21
forum: General Help
---

### Post by Moose on 2012-08-21
I have downloaded WBAR for Ubuntu. I don't have acess to the internet at the moment until i fix some wifi driver issues. I can't do auto install with software centre because it needs internet connection.. The installer came in a .deb package (it was called wbar_2.3.0-1_i386.deb) Now i opened it with archive manager and saw 3 folders. I know where two of them go (one was usr and i think the other was etc) But there was a third folder called Debian. Where do i put this folder? Or is there a way i can install the program from the .deb archive using the Terminal? If anyone can help me with this that would be much appreciated.

---

### Post by papibe on 2012-08-21
Hi AnarchyTech.

Instead of double clicking the file, right click on it and there should be other options like 'Open with package installer' or similar.

Tell us how it goes.
Regards.

---

### Post by Moose on 2012-08-21
> **papibe said:**
> Hi AnarchyTech.
 
Instead of double clicking the file, right click on it and there should be other options like 'Open with package installer' or similar.
 
Tell us how it goes.
Regards.
 Hey, I can't try your method at the moment because im at school, But from memory i don't think there is a package installer option. Im using Ubuntu 11.10. I will double check when i get home though. Yeah i know that sounds silly, asking how to do it when im not even at home. But i had some spare time. ^_^ Thanks for helping though.

---

### Post by elliotn on 2012-08-22
open the deb with Ubuntu software center but am sure u gona face a dependency problem

---

### Post by mzaam on 2012-08-22
> **elliotn said:**
> open the deb with Ubuntu software center but am sure u gona face a dependency problem
USC will not allow you hit install button when u dont connect to internet, i suggest to install gdebi and install your package with it, but i think u'll get  dependency problem

---

### Post by drmrgd on 2012-08-22
I'm not sure about Software Center's needs for the internet to install local packages.  If it's the case, then I think you can install it via the command line the old fashioned way.  Just run:

```
sudo dpkg -i wbar_2.3.0-1_i386.deb
```

The Debian package manager will take over an install from there.  

As other's say, you might run into dependency problems.  According to the Precise Package information, you'll need as dependencies:

[http://packages.ubuntu.com/ca/precise/wbar](http://packages.ubuntu.com/ca/precise/wbar)

- [libc6]("http://packages.ubuntu.com/ca/precise/libc6") 	 (>= 2.4)
- [libgcc1]("http://packages.ubuntu.com/ca/precise/libgcc1") 	 (>= 1:4.1.1)
- [libimlib2]("http://packages.ubuntu.com/ca/precise/libimlib2")
- [libstdc++6]("http://packages.ubuntu.com/ca/precise/libstdc++6") 	 (>= 4.4.0)
- [libx11-6]("http://packages.ubuntu.com/ca/precise/libx11-6")

I suppose you could manually try to install all of those packages as well (assuming you don't have some of them already).  Of course, that could end up being one really large fall down the rabbit hole as you try to sort out dependencies of the dependencies!  You might work out the WiFi problem first just to make your life easier.

---

### Post by Moose on 2012-08-22
> **drmrgd said:**
> I'm not sure about Software Center's needs for the internet to install local packages. If it's the case, then I think you can install it via the command line the old fashioned way. Just run:
 
```
sudo dpkg -i wbar_2.3.0-1_i386.deb
```
 
The Debian package manager will take over an install from there. 
 
As other's say, you might run into dependency problems. According to the Precise Package information, you'll need as dependencies:
 
[http://packages.ubuntu.com/ca/precise/wbar](http://packages.ubuntu.com/ca/precise/wbar)
 
- [libc6]("http://packages.ubuntu.com/ca/precise/libc6")      (>= 2.4)
- [libgcc1]("http://packages.ubuntu.com/ca/precise/libgcc1")      (>= 1:4.1.1)
- [libimlib2]("http://packages.ubuntu.com/ca/precise/libimlib2")
- [libstdc++6]("http://packages.ubuntu.com/ca/precise/libstdc++6")      (>= 4.4.0)
- [libx11-6]("http://packages.ubuntu.com/ca/precise/libx11-6")
 
I suppose you could manually try to install all of those packages as well (assuming you don't have some of them already). Of course, that could end up being one really large fall down the rabbit hole as you try to sort out dependencies of the dependencies! You might work out the WiFi problem first just to make your life easier.
Cheers. I will fix my wifi first.

---

