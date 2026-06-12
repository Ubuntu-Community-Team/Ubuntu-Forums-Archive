---
title: "Java installation troubles."
date: 2010-04-15
forum: General Help
---

### Post by seandude on 2010-04-15
[FONT="Arial"]I'm trying to install the java jdk, but for some reason, when I try to install, I get this message.  
[/FONT]

[FONT="Courier New"]
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
[/FONT]

The problem is, is that I've got 9.10 installed, and I don't think I have the unstable version of anything.  Can anyone help?

---

### Post by philinux on 2010-04-15
> **seandude said:**
> [FONT="Arial"]I'm trying to install the java jre, but for some reason, when I try to install, I get this message.  
[/FONT]

[FONT="Courier New"]
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
[/FONT]

The problem is, is that I've got 9.10 installed, and I don't think I have the unstable version of anything.  Can anyone help?Open synaptic and use edit>fix broken.

---

### Post by seandude on 2010-04-15
Synaptic says that it's fixed all dependencies, but when I try to install the jdk it says that there are unresolvable dependencies.  All of my repositories are set up for karmic, so I'm really not sure what's wrong.

---

### Post by seandude on 2010-04-15
I found another thread that has a solution.  It says to downgrade to lower versions of jre and bin packages.  Is this a good idea?

[http://ubuntuforums.org/showthread.php?t=1342385](http://ubuntuforums.org/showthread.php?t=1342385)

---

### Post by philinux on 2010-04-15
Try this and report back any errors.

```
sudo apt-get update && sudo apt-get upgrade

then

sudo dpkg --configure -a


```

---

### Post by seandude on 2010-04-15
it installed, but when I ran `java -version`, it said that I'm running 'java version "1.6.0_0"'.  Shouldn't it be 1.6.15 or 1.6.17?

---

