---
title: "Installing Java Run Time from Sun"
date: 2006-02-27
forum: General Help
---

### Post by geniusvicks on 2006-02-27
Please tell me how to install JRE.

---

### Post by knalle on 2006-02-27
First you will need to add all the extra repositories for Ubuntu. (ie Multiverse, Universe...) Please see other how to's on how to do that.

Now go to Sun's website [http://java.sun.com/](http://java.sun.com/) and select the java jdk or jre that you want.

This example uses J2jsdk-1.4.2 but you can use any J2sdk. Run similar commands from the terminal:

First install the required packages:

sudo apt-get install fakeroot java-package java-common

Create the Deb file for the install:

fakeroot make-jpkg sun-j2sdk-1.4.2_10-linux-i586.bin

Install The deb file

sudo dpkg -i sun-j2sdk-1.4.2_10_i386.deb

Now make Sun's java the default by running this command and selecting it.

sudo update-alternatives --config java

you can now check your java sdk with:

java -version

java version "1.4.2_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_10-b03)
Java HotSpot(TM) Client VM (build 1.4.2_10-b03, mixed mode)

Happy Hacking!

---

### Post by Ramses de Norre on 2006-02-27
[http://ubuntuforums.org/showthread.php?t=76754]("http://ubuntuforums.org/showthread.php?t=76754") 
Just change the version number in all the commands (the one from the site is newer as the one discribed).

---

