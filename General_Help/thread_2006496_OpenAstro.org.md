---
title: "OpenAstro.org"
date: 2012-06-19
forum: General Help
---

### Post by Gael33 on 2012-06-19
I recently installed the deb package (all dependencies satisfied) OpenAstro.org Astrology software for my partner to use. It installed okay, and showed up in the start menu. However, the program refuses to start. I have no idea why and I was hoping that someone could help me with this? I have checked the OpenAstro site and have assured myself that all the dependencies are there. To all intents and purposes, this program should work ... but it doesn't. I even uninstalled it and downloaded another deb package thinking that the first one may have been faulty ... sadly, same result.
I would be grateful for any help to fix this, or alternatively another program that will work.  

gael. (non-tech) 

Ubuntu 12.04 64 bit

---

### Post by coffeecat on 2012-06-19
I'm not sure that I'll be able to help, but I want to pick up one point. You say that you're running 12.04 and that you were able to install it with all dependencies satisfied. If you look at the [PPA page]("https://launchpad.net/~pellesimon/+archive/ppa"), or the [download page at the openastro site]("http://openastro.org/?Download"), you'll see that there are deb packages for versions of Ubuntu up to Oneiric (11.10), but not 12.04. Out of interest, I downloaded the 64-bit Oneiric deb and tried to install it in 12.04, but I got a "Dependency is not satisfiable: python2.6" message and it would not install. 12.04 comes with python2.7, not python2.6. 

So - how did you manage to install the deb package?  Also, you say the program refuses to start. This following probably won't work to launch the program but it may reveal a useful error message. Open a terminal, and:

```
openastro.py
```

**EDIT**: This is the depends section of the control file in the Oneiric deb:

> [noparse]Depends: python (<< 2.8), python (>= 2.6), python-central (>= 0.6.11), python2.6, libc6 (>= 2.7), python-gtk2, python-dateutil, python-rsvg, python-cairo (>= 1.2.0), imagemagick[/noparse]

As you can see it depends specifically on python2.6 (not to be confused with the separate package python).

---

### Post by Gael33 on 2012-06-19
Thank you for your quick and positive response :)
I installed python 2.6.1 after getting the same error message as yourself. After installing I then found I was able to install OpenAstro with all dependencies satisfied yet still without success.
Do you think that python 2.7 is stopping the program from running and if so should I remove it?
I await your reply.

gael

---

### Post by coffeecat on 2012-06-19
That's interesting. I'll do some investigating - this has intrigued me - and post back in a few hours.

---

### Post by coffeecat on 2012-06-19
> **Gael33 said:**
> 
I installed python 2.6.1 after getting the same error message as yourself. 

[noparse]No, I'm chasing moonbeams at the moment. We need to clarify something. The package python (version 2.7.3 in 12.04) is different from the package python2.6 or python2.7. You specifically need python2.6 in order to be able to install openastro (as well as python version >=2.6, <2.8), and python2.6 is not in the 12.04 repository, only python2.7. It's confusing, I know. Where did you get the "python 2.6.1" package from? Can you provide a download link?[/noparse]

---

### Post by Gael33 on 2012-06-19
> **coffeecat said:**
> [noparse]No, I'm chasing moonbeams at the moment. We need to clarify something. The package python (version 2.7.3 in 12.04) is different from the package python2.6 or python2.7. You specifically need python2.6 in order to be able to install openastro (as well as python version >=2.6, <2.8), and python2.6 is not in the 12.04 repository, only python2.7. It's confusing, I know. Where did you get the "python 2.6.1" package from? Can you provide a download link?[/noparse]

[http://www.oldapps.com/Python.php?old_python=26](http://www.oldapps.com/Python.php?old_python=26)

Thanks,

gael

---

### Post by coffeecat on 2012-06-19
I don't think that package is suitable. Always install repository packages when you can. I've tried installing the repository python2.6 package + dependencies in 12.04, but "openastro.py" from the terminal gives me an error. I somewhat doubt that openastro will work in 12.04 - the PPA maintainer would need to build a version specifically for 12.04.

I've tried it in 11.10, and it works just fine in that version of Ubuntu which doesn't really help you. 

You didn't say which openastro package you installed, nor the output of "openastro.py".

---

### Post by Gael33 on 2012-06-19
> **coffeecat said:**
> I don't think that package is suitable. Always install repository packages when you can. I've tried installing the repository python2.6 package + dependencies in 12.04, but "openastro.py" from the terminal gives me an error. I somewhat doubt that openastro will work in 12.04 - the PPA maintainer would need to build a version specifically for 12.04.

I've tried it in 11.10, and it works just fine in that version of Ubuntu which doesn't really help you. 

You didn't say which openastro package you installed, nor the output of "openastro.py".

Coffeecat, thank you for trying ... I will install 11.10 on an old machine and give it another go at the weekend :)

gael

---

### Post by coffeecat on 2012-06-19
Sorry I couldn't help getting this to work in 12.04. There is one other suggestion. You could contact the PPA maintainer and ask if they have any plans to compile a package suitable for 12.04. PPA page here:

[https://launchpad.net/~pellesimon/+archive/ppa](https://launchpad.net/~pellesimon/+archive/ppa)

Click on the Pelle van der Scheer link to go to their Launchpad page. If you have a Launchpad account yourself and you are logged in, there will be a "contact this user" link to send an email.

---

### Post by Gael33 on 2012-06-19
> **coffeecat said:**
> Sorry I couldn't help getting this to work in 12.04. There is one other suggestion. You could contact the PPA maintainer and ask if they have any plans to compile a package suitable for 12.04. PPA page here:

[https://launchpad.net/~pellesimon/+archive/ppa](https://launchpad.net/~pellesimon/+archive/ppa)

Click on the Pelle van der Scheer link to go to their Launchpad page. If you have a Launchpad account yourself and you are logged in, there will be a "contact this user" link to send an email.

Yes, I have an account ... and I have just sent him an email.

gael.

---

### Post by rudregues on 2012-06-23
Hey Gael33, nice thread. I was trying to install openastro and failed, then found this post. Could you post here if the PPA maintainer have plans to compile a precise version of the package? Last case, I'll run the openastro in a virtual machine.

 [ ]'s

---

### Post by dradak1 on 2012-08-27
I was looking for same thing and problem is coming from python most-likely somebody will find a solution. On mean time I install under wine AstroWin & AstroClk from following website: [http://www.astrowin.org/astrology_software.php](http://www.astrowin.org/astrology_software.php). 
That can be temporary solution. ;)

---

### Post by rudregues on 2012-09-02
> **dradak1 said:**
> I was looking for same thing and problem is coming from python most-likely somebody will find a solution. On mean time I install under wine AstroWin & AstroClk from following website: [http://www.astrowin.org/astrology_software.php](http://www.astrowin.org/astrology_software.php). 
That can be temporary solution. ;)

Thanks for replying dradak, I've solved by downloading the and editing the amd64 11.10 ubuntu .deb package directly from openastro website [http://www.openastro.org/?Download](http://www.openastro.org/?Download)

Steps:
1- Go to the directory you downloaded
```
cd /download_directory
```2- Extract informations form .deb package 
 ```
dpkg-deb -e openastro.org_1.1.25-0ubuntu1~oneiric_amd64.deb /download_directory/openastro.org_1.1.25-0ubuntu1~precise_amd64/DEBIAN

```3- Extract script install etc from .deb:
```
dpkg-deb -x openastro.org_1.1.25-0ubuntu1~oneiric_amd64.deb /download_directory/openastro.org_1.1.25-0ubuntu1~precise_amd64
```4- Correct dependencies:
```
gedit /download_directory/openastro.org_1.1.25-0ubuntu1~precise_amd64/DEBIAN/control
``` edit "Depends" line, replacing:
[COLOR=Red]python2.6[/COLOR]
by
[COLOR=Red]python2.7[/COLOR]

4- Correct the executable script:
```
gedit /download_directory/openastro.org_1.1.25-0ubuntu1~precise_amd64/DEBIAN/usr/bin/openastro.py
```change first line to:
#!/usr/bin/[COLOR=Red]python2.7[/COLOR]

5- Build our .deb package:
dpkg-deb -b /download_directory/openastro.org_1.1.25-0ubuntu1~precise_amd64/

6- Open with Software Center and install to enjoy! :-)

P.S.: the bug on launchpad: [https://bugs.launchpad.net/openastro.org/+bug/963771](https://bugs.launchpad.net/openastro.org/+bug/963771)

   [ ]'s

---

### Post by rudregues on 2013-01-14
It seems that the bug was fixed [https://bugs.launchpad.net/openastro.org/+bug/963771](https://bugs.launchpad.net/openastro.org/+bug/963771)

  [ ]'s

---

