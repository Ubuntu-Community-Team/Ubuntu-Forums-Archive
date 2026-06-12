---
title: "I'm having trouble installing packages and I'm not sure why."
date: 2012-07-20
forum: General Help
---

### Post by picklemaster246 on 2012-07-20
Whenever I attempt to install or remove packages via apt-get (like removing Firefox or installing Pidgin), I get dependency errors.  This all started when I tried to install Cinnamon from the official PPA, which gave me this output:

```
gerrit@picklhaus:~$ sudo apt-get install cinnamon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cinnamon : Depends: gir1.2-clutter-1.0 but it is not going to be installed
            Depends: gir1.2-cogl-1.0 but it is not going to be installed
            Depends: gir1.2-coglpango-1.0 but it is not going to be installed
            Depends: gir1.2-folks-0.6 but it is not going to be installed
            Depends: gir1.2-gee-1.0 but it is not going to be installed
            Depends: gir1.2-json-1.0 but it is not going to be installed
            Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: gir1.2-networkmanager-1.0 but it is not going to be installed
            Depends: gir1.2-telepathyglib-0.12 but it is not going to be installed
            Depends: gir1.2-telepathylogger-0.2 but it is not going to be installed
            Depends: gjs (>= 1.29.18) but it is not going to be installed
            Depends: libgjs0-
            Depends: libgjs0c (>= 1.32.0) but it is not going to be installed
            Depends: libmozjs185-1.0 (>= 1.8.5-1.0.0) but it is not going to be installed
            Depends: caribou but it is not going to be installed
            Depends: cups-pk-helper but it is not going to be installed
            Depends: gir1.2-accountsservice-1.0 but it is not going to be installed
            Depends: gir1.2-gkbd-3.0 but it is not going to be installed
            Depends: gir1.2-polkit-1.0 but it is not going to be installed
            Depends: gir1.2-upowerglib-1.0 but it is not going to be installed
            Depends: mesa-utils but it is not going to be installed
            Recommends: gnome-themes-standard but it is not going to be installed
            Recommends: gnome-session-fallback but it is not going to be installed
 libmuffin0 : Depends: libcogl5 (>= 1.7.4) but it is not installable
              Depends: muffin-common (= 1.0.2) but 1.0.3-UP1-0ubuntu1~precise1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So then I try the apt-get -f install command, which gives me this:

```
gerrit@picklhaus:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmuffin0
The following packages will be upgraded:
  libmuffin0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/543 kB of archives.
After this operation, 122 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libmuffin0:
 libmuffin0 depends on libcogl5 (>= 1.7.4); however:
  Package libcogl5 is not installed.
 libmuffin0 depends on muffin-common (= 1.0.2); however:
  Version of muffin-common on system is 1.0.3-UP1-0ubuntu1~precise1.
dpkg: error processing libmuffin0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libmuffin0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I googled libmuffin0 and I found out that it's part of a window manager called muffin, which I attempt to install here:

```
gerrit@picklhaus:~$ sudo apt-get install muffin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmuffin0 : Depends: libcogl5 (>= 1.7.4) but it is not installable
              Depends: muffin-common (= 1.0.2) but 1.0.3-UP1-0ubuntu1~precise1 is to be installed
 muffin : Depends: libmuffin0 (>= 1.0.3) but 1.0.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So we've come full-circle, I think.  I should note I'm dualbooting Ubuntu and Win7 and I've only created the root, home, and swap partitions because I'm planning on store most stuff on the Windows partition.  Any help is appreciated.

---

### Post by plucky on 2012-07-20
What version of Ubuntu are you running?

Have you run ```
sudo apt-get update
``` after you added the PPA?

Good Luck

---

### Post by picklemaster246 on 2012-07-20
12.04 LTS, and yes, many times

---

### Post by picklemaster246 on 2012-07-21
i do suppose i should have worded the title more attractively

---

### Post by plucky on 2012-07-22
> **picklemaster246 said:**
> 12.04 LTS, and yes, many times

Post your sources.list ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

Run those two commands in a terminal and post the output.

---

