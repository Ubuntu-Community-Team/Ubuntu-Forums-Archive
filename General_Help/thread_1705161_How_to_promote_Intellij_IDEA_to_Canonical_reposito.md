---
title: "How to promote Intellij IDEA to Canonical repositories?"
date: 2011-03-11
forum: General Help
---

### Post by anatolik on 2011-03-11
[Intellij IDEA]("http://www.jetbrains.com/idea/") is IMHO the best Java IDEA. And Debian/Ubuntu users miss a lot not having it in the official repositories.

Personally I use this script [https://github.com/anatol/intellij-idea-dpkg](https://github.com/anatol/intellij-idea-dpkg) that allows me to build *.deb package automatically using dpkg-deb tool. It is done automatically and saves a lot of time to me.

There are several requests to Intellij to make an official repository for its products like this one [http://youtrack.jetbrains.net/issue/IDEA-63004](http://youtrack.jetbrains.net/issue/IDEA-63004) but Intellij does not pay much attention to it (I guess most of their developers use Windows and do not know what does it mean to have a *real* package manager).

My question - what is the best way to promote the opensource Intellij products to the official Ubuntu repository? Create a PPA first?

I am not an expert in deb maintenance (I would like to get some help from you guys). I built *.deb using the script (see url above) and it looks like dpkg-deb does not produce *.changes file needed for PPA. What is the best way to create this *.changes file?

PS if you try to run the script please use
./build-package -f IC -p debian

---

### Post by lykeion on 2011-03-12
I totally agree with you that IntelliJ is the best Java IDE. 

Installing it is really easy; just download the tarball from the homepage, unpack it in your home dir, edit the start script idea.sh to export the JDK_HOME path, and you're good to go.

And personally I prefer installing it this way rather than having a deb package.

EDIT
Saw that you already posted this question long time ago [here]("http://ubuntuforums.org/showthread.php?t=1448357")
And regarding PPA/Debian packaging you already got an answer:
> Please note you cannot distribute the intellij idea files since that is not allowed by it's license, so uploading it to a public PPA would put you in breach of the license.

---

### Post by anatolik on 2011-03-12
> **lykeion said:**
> Installing it is really easy; just download the tarball from the homepage, unpack it in your home dir, edit the start script idea.sh to export the JDK_HOME path, and you're good to go.
Yeah, I know how to install it - I did it dozen times with EAP's. That is why I want simpler way, like

$ sudo apt-get install intellij-idea-ic

> **lykeion said:**
> Saw that you already posted this question long time ago [here]("http://ubuntuforums.org/showthread.php?t=1448357")
And regarding PPA/Debian packaging you already got an answer:
True, you cannot redistribute it. That is why there are only 2 ways possible:
- convenience Intellij to have their own official repository (or, less realistic, make them Canonical partners and put their debs to official Canonical repositories)
- Put into installer a script that downloads distribution from the Intellij site and install it. I think it is what Flash installer does with Abode proprietary software. There is actually (unmaintained) PPA that implements it [https://launchpad.net/~yannickm/+archive/intellij-idea-eap](https://launchpad.net/~yannickm/+archive/intellij-idea-eap)

---

