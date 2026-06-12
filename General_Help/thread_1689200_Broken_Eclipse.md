---
title: "Broken Eclipse"
date: 2011-02-16
forum: General Help
---

### Post by kronozord on 2011-02-16
I  tried to update my eclipse to the Helios version through a [PPA]("https://launchpad.net/%7Eeclipse-team/+archive/debian-package"), but I wanted to use it  for programming in C / C++, in order to integrate it with the NS-3. After  updating CDT installed the plugin but could not create project in C / C  + + because they did not appear in the File -> New -> Project. I decided to return to the previous version to see the eclipse in the repositories by default.


I did:

```
sudo apt-get purge eclipse*
sudo apt-get autoclean
sudo apt-get autoremove
```Removed the  PPA repos from the lista and then i did:

```
sudo apt-get update
sudo apt-get upgrade
```Ive tried to reinstall eclipse through

```
sudo apt-get install eclipse
``````
bash told me this:

The following packages have unmet dependencies:
 eclipse : Depends: eclipse-jdt (>= 3.5.2-6ubuntu1.1) but it is not going to be installed
           Depends: eclipse-pde (>= 3.5.2-6ubuntu1.1) but it is not going to be installed
E: Broken packages
```Help please.

---

### Post by johnDonson on 2011-02-25
Hello,

Same here. The Android guys are also mad about this.
[http://forum.xda-developers.com/showthread.php?t=806190](http://forum.xda-developers.com/showthread.php?t=806190)

In my case every add-on I had installed in Eclipse dissapeared after 10.04 to 10.10 update :confused:

---

