---
title: "Updating kdelibs"
date: 2010-11-25
forum: General Help
---

### Post by doriad on 2010-11-25
When trying to install some software I am getting:
```

ERROR: the installed kdelibs version 4.4.2 is too old, at least version 4.5.0 is required

```

I tried
```

sudo apt-get update

```

and

```

sudo apt-get upgrade

```

but it didn't seem to help.

I also tried this:
```


doriad@davidlaptop:~/bin/kdevplatform$ sudo apt-get install kde-libs
[sudo] password for doriad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde-libs
doriad@davidlaptop:~/bin/kdevplatform$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
doriad@davidlaptop:~/bin/kdevplatform$ sudo apt-get install kdelibs*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting kdelibs4-dbg for regex 'kdelibs*'
Note, selecting kdelibs4c2a for regex 'kdelibs*'
Note, selecting kdelibs4-dev for regex 'kdelibs*'
Note, selecting kdelibs4c2a-dbg for regex 'kdelibs*'
Note, selecting kdelibs4c2 for regex 'kdelibs*'
Note, selecting kdelibs4c2-dbg for regex 'kdelibs*'
Note, selecting kdelibs-data for regex 'kdelibs*'
Note, selecting kdelibs4 for regex 'kdelibs*'
Note, selecting kdelibs5 for regex 'kdelibs*'
Note, selecting kdelibs5-dbg for regex 'kdelibs*'
Note, selecting kdelibs5-dev for regex 'kdelibs*'
Note, selecting kdelibs5-doc for regex 'kdelibs*'
Note, selecting kdelibs5-data for regex 'kdelibs*'
Note, selecting kdelibs-bin for regex 'kdelibs*'
Note, selecting kdelibs-dbg for regex 'kdelibs*'
Note, selecting kdelibs-dev for regex 'kdelibs*'
Note, selecting kdelibs4-dev instead of kdelibs-dev
Note, selecting kdelibs for regex 'kdelibs*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs-dbg: Depends: qt-x11-free-dbg but it is not going to be installed
  kdelibs5-dev: Conflicts: kdelibs4-dev but 4:3.5.10.dfsg.1-3ubuntu2.10.04.1 is to be installed
E: Broken packages

```

Any thoughts on how to get kdelibs 4.5?

David

---

### Post by doriad on 2011-02-19
Any thoughts on this?

---

### Post by gmargo on 2011-02-19
From the 4.4.2 version number, I assume you are running 10.04 Lucid.

10.10 Maverick uses the 4.5.1 version, so one option is to upgrade to Maverick.

You might be able to load backported 4.5.3 onto Lucid from this ppa:
[https://launchpad.net/~kubuntu-ppa/+archive/backports]("https://launchpad.net/%7Ekubuntu-ppa/+archive/backports")

---

