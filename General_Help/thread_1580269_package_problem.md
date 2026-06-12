---
title: "package problem"
date: 2010-09-23
forum: General Help
---

### Post by alefilly on 2010-09-23
i have to install libc-client-dev
 
apt-get install libc-client-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
libc-client-dev: Depends: libc-client2002edebian (= 7:2002edebian1-13) but it is not going to be installed
Depends: libpam0g-dev but it is not going to be installed
libpam-modules: PreDepends: libpam0g (>= 1.1.0) but 1.0.1-9ubuntu1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 
if i try 
apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
...
VERY VERY VERY VERY long list of packages
...
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
base-files libpam-modules (due to base-files) bash e2fsprogs libblkid1 (due to e2fsprogs) libuuid1 (due to e2fsprogs) hostname upstart (due to hostname) login libpam0g (due to
login) libpam-runtime (due to login) mount util-linux
0 upgraded, 0 newly installed, 615 to remove and 3 not upgraded.
After this operation, 1,788MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
?]
 
i don't want to remove all this packages... what i have to do?

---

### Post by zvacet on 2010-09-23
If you don´t want to remove these packages then

```
sudo apt-get install package1 package2
```

Of course you will do this with your packages marked for removal.After that you will never be asked for removal of those packages.You have some package witch are not upgraded.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by alefilly on 2010-09-23
mmmm... what's wrong?
 
apt-get install base-files libpam-modules bash e2fsprogs libblkid1 libuuid1 hostname upstart login libpam0g libpam-runtime mount util-linux
Reading package lists... Done
Building dependency tree
Reading state information... Done
base-files is already the newest version.
libpam-modules is already the newest version.
bash is already the newest version.
e2fsprogs is already the newest version.
libblkid1 is already the newest version.
libuuid1 is already the newest version.
hostname is already the newest version.
upstart is already the newest version.
login is already the newest version.
libpam0g is already the newest version.
libpam-runtime is already the newest version.
mount is already the newest version.
util-linux is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libpam-modules: PreDepends: libpam0g (>= 1.1.0) but 1.0.1-9ubuntu1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by QLee on 2010-09-23
[QUOTE=alefilly]mmmm... what's wrong?[/QUOTE]
When I get an error printout while trying to install I read it to see if it suggests anything.
 
[QUOTE=alefilly]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/QUOTE]

This last line looks relevant, eh?

Did you remember to do an apt-get update, to refresh your packages list, before you tried to install?

---

### Post by alefilly on 2010-09-23
> **alefilly said:**
> i have to install libc-client-dev
 
if i try 
**apt-get -f install**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
...
VERY VERY VERY VERY long list of packages
...
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
base-files libpam-modules (due to base-files) bash e2fsprogs libblkid1 (due to e2fsprogs) libuuid1 (due to e2fsprogs) hostname upstart (due to hostname) login libpam0g (due to
login) libpam-runtime (due to login) mount util-linux
0 upgraded, 0 newly installed, 615 to remove and 3 not upgraded.
After this operation, 1,788MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
?]

 
> **QLee said:**
> 
When I get an error printout while trying to install I read it to see if it suggests anything.

when i reply to post i read entire thread....
 
 
of course i have refresh and update...

---

### Post by QLee on 2010-09-23
Which version are you running, that's a library from jaunty.

---

### Post by alefilly on 2010-09-23
ubuntu 9.10
2.6.31-20-server

---

### Post by QLee on 2010-09-23
[QUOTE=alefilly]ubuntu 9.10
2.6.31-20-server[/QUOTE]

Sorry to take so long getting back to this, I'm somewhat surprised that no one else offered to help, usually I can't type fast enough to reply to posts before someone else does and this time I've been gone for a few hours. I see you are new here and we haven't said welcome yet, so welcome to the forums!

So, the version that you are running is 9.10 (Karmic Koala), yet your package manager is erroring because it cannot install the pam library from 9.10, "libpam0g (>= 1.1.0) but 1.0.1-9ubuntu1.1 is to be installed, that's the version from Jaunty. We will need to determine why the system isn't trying to install the version for your version of Ubuntu.

Was this system previously an earlier version (i.e. 9.04) that was upgraded? If so, what upgrade path did you follow?

Where did you get the libc-client-dev package, and is that the full package name?

You might choose to post your /etc/apt/sources.list so we can determine if anything is incorrect in there.

---

### Post by alefilly on 2010-09-24
thanks for your help!
i have no urgency to resolve this problem but i am stuck and i can not go on.
 
this is entire history....
i need to install imap modules for php5, but when i compile php source i retrive this error
"configure: error: utf8_mime2text() has new signature, but U8T_CANONICAL is missing. This should not happen. Check config.log for additional information."
 
i found that i need to install:
apt-get install libc-client-dev
 
to try to fix this problem i have installed this package 
sudo dpkg -i libpam0g_1.0.1-9ubuntu1.1_amd64.deb
 
 
 
source file
## Repository ubuntu
##
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
##
## Sorgenti Ubuntu
##
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
##
## Repository Partner Canonical
##
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
##
## Medibuntu
##
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb [http://www.pvv.ntnu.no/~knuta/xmms/intrepid](http://www.pvv.ntnu.no/~knuta/xmms/intrepid) ./
##
##added by ale
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) dapper main universe

---

### Post by zvacet on 2010-09-24
```
gksudo gedit /etc/apt/sources.list
```

and remove

deb [http://www.pvv.ntnu.no/~knuta/xmms/intrepid]("http://www.pvv.ntnu.no/%7Eknuta/xmms/intrepid") ./
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) dapper main universe 	

Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

After that upgrade to Karmic,because you are still running Jaunty,

---

### Post by alefilly on 2010-09-24
done, now i am under 10.04
 
i have the same error when compile php
"configure: error: utf8_mime2text() has new signature, but U8T_CANONICAL is missing. This should not happen. Check config.log for additional information."
 
then i go to install libc-client-devel
but now it "Couldn't find package libc-client-devel"
i have to add some repository?

---

### Post by QLee on 2010-09-24
[QUOTE=alefilly]...
then i go to install libc-client-devel
but now it "Couldn't find package libc-client-devel"
...[/QUOTE]
That's why I asked you, where did you get that package and if that was the full name. I don't find a package with that name, there must be more to it.

---

### Post by zvacet on 2010-09-24
System>admin>software sources>check all under Ubuntu software (excwpt source) and first two unser updates tab.Refresh.Now find in synaptic libc-client-dev.

---

### Post by QLee on 2010-09-24
Well zvacet, since alefilly is running a server kernel, there is a possibility that the GUI you suggest won't run, most sys admins don't want X on a server.

apt-cache showpkg libc-client-dev, from the CLI might be a better choice to get that information.

---

### Post by zvacet on 2010-09-24
@ **QLee**

You are right.I missed that he is using server.Thanks for correcting me.

---

### Post by alefilly on 2010-09-27
thanks!
after the update, I could install that package
and finally the compilation was done with success
 
very very thanks guys!

---

