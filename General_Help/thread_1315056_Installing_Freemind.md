---
title: "Installing Freemind"
date: 2009-11-04
forum: General Help
---

### Post by ecpepper on 2009-11-04
A few months back--while running 9.04--I installed a copy of the latest version of freemind from the .deb available at sourceforge (the version in the ubuntu repos lacking some features that I require).

Yesterday, I did a fresh install of 9.10 and tried, afterwards, to install that same .deb version of freemind. It didn't work. I am getting the error message "Error: Dependency is not satisfiable: librelaxng-datatype-java"

I have JRE6 installed (through ubuntu-restricted-extras) but apparently not this package. Any thoughts on what has changed/gone wrong? Or better, how to fix it?

ecpepper

---

### Post by mikewhatever on 2009-11-05
Apparently, Karmic doesn't have librelaxng-datatype-java package in its repositories. Perhaps manually downloading and installing it from Jaunty might work.
[http://packages.ubuntu.com/jaunty/librelaxng-datatype-java](http://packages.ubuntu.com/jaunty/librelaxng-datatype-java)

---

### Post by daqron on 2009-11-05
Same problem here. Would really like to use version 8 but it seems incompatible with karmic. Version 7, however, is available in the "Ubuntu Software Center".

Possibly useful feedback from terminal:

```
The following packages have unmet dependencies:
  freemind: Depends: librelaxng-datatype-java but it is not installable

Package librelaxng-datatype-java is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package librelaxng-datatype-java has no installation candidate
```
Cross-posted here:
[https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/212588](https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/212588)

Cheers,
Jeremy

---

### Post by catshout on 2009-11-11
>  	 		**Re: Installing Freemind**
 Apparently, Karmic doesn't have librelaxng-datatype-java package in its repositories. Perhaps manually downloading and installing it from Jaunty might work.
[http://packages.ubuntu.com/jaunty/li...-datatype-java]("http://packages.ubuntu.com/jaunty/librelaxng-datatype-java")

I tried to install the librelaxng-datatype-java package first and Freemind 0.8 afterwards, this works ..

---

### Post by daqron on 2009-11-11
Solution posted over on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/212588"):
[QUOTE="AnGus"]I solved the problem by borrowing on the advice of others:

1. Added JAVA_HOME="/usr/lib/jvm/java-6-sun/" to /etc/environment file (see Katerine 2008-12-09 above)
2. Installed freemind_0.9.0RC4-0ubuntu1_all.deb ([https://launchpad.net/~igorgomes/+archive/ppa/+files/freemind_0.9.0RC4-0ubuntu1_all.deb](https://launchpad.net/~igorgomes/+archive/ppa/+files/freemind_0.9.0RC4-0ubuntu1_all.deb)) as referred to in Re: [Bug 182927] Re: Update FreeMind to 0.9.0 RC4 by Igor[/QUOTE]

---

### Post by ardugh on 2009-11-23
> **daqron said:**
> Solution posted over on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/212588"):

To all those with a freemind :-)

I also successfully installed rc4 in Ubuntu 9.10 by following the advice in the above message. Thanks for sharing this :popcorn:

---

### Post by eyerouge on 2010-03-30
> **ardugh said:**
> I also successfully installed rc4 in Ubuntu 9.10 by following the advice in the above message.

Same here :)

---

### Post by focaccio on 2010-04-05
Thanks a million to daqron for the link

That .deb package is exactly what I needed since the FreeMind package I find in synaptic on my 9.10 system is not the FreeMind .9 RC4 that I need.

The .deb package from the link above worked perfectly on my system. FreeMind launches and works!!! I had previously installed the JRE 6 with synaptic.

No extra steps were necessary. Sweet!

---

### Post by focaccio on 2010-05-11
Here is another resource for FreeMind .deb packages:
[http://packages.debian.org/sid/all/freemind/download]("http://packages.debian.org/sid/all/freemind/download")

I just successfully installed 0.9rc6 FreeMind from a .deb download from this site after first installing jre6 with synaptic.

---

### Post by patrickcage on 2010-05-31
> **mikewhatever said:**
> Apparently, Karmic doesn't have librelaxng-datatype-java package in its repositories. Perhaps manually downloading and installing it from Jaunty might work.
[http://packages.ubuntu.com/jaunty/librelaxng-datatype-java](http://packages.ubuntu.com/jaunty/librelaxng-datatype-java)

This worked for me! ;-)

---

### Post by CalvinK on 2010-10-29
> **daqron said:**
> Solution posted over on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/212588"):
This tip is very useful. Caution ! I had a problem when installing Maverick. My /etc/environment file looked like that :
[I]# begin
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.07/
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.07/bin/"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"
# end
[/I]
Unfortunately the directory /java-6-sun-1.6.0.07 didn't exist entailing an error. Just replace these lines

[I]# begin
JAVA_HOME=/usr/lib/jvm/java-6-sun/
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun/bin/"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"
# end
[/I]
et voilà ! freemind works again.

---

### Post by jfmxl on 2010-12-28
following focaccio... no problems.

---

