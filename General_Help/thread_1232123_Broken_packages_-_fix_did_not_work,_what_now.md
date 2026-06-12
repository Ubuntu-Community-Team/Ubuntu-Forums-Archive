---
title: "Broken packages - fix did not work, what now?"
date: 2009-08-05
forum: General Help
---

### Post by AlexsAntidote on 2009-08-05
Monday night I did an update and near the end of the update Firefox crashed and I got a crash report, but the crash report was for the update (firefox was on the list of updates, but from what I could tell wasn't the problem). 

I don't recall the specific message, but I opened terminal and did:

sudo apt-get clean
sudo apt-get update
sudo apt-get -f install

here's the results:

```
alex@notebook:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libnspr4-dev
The following NEW packages will be installed:
  libnspr4-dev
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0B/263kB of archives.
After this operation, 1454kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 369250 files and directories currently installed.)
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.5-0ubuntu0.9.04.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libnspr4-dev_4.7.5-0ubuntu0.9.04.1_i386.deb (--unpack):
 trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4-dev_4.7.5-0ubuntu0.9.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried renaming nspr.m4 and rerunning the fix but that didn't work so I renamed it back.

Any ideas? (I also tried using synaptic to fix it, but that failed also, which was no surprise).

---

### Post by FogAudio on 2009-08-05
I am having the exact same issue. I tried updating to Firefox 3.5 yesterday and it has been nothing but trouble.

Running: Kubuntu JJ, Firefox3.5

After more troubles tried installing latest Adobe Flash from Adobe's site then started getting issue regarding Netscape Portable Runtime (nspr).

---

### Post by FogAudio on 2009-08-05
Hmmm... NSPR had a dependency conflict with Kompozer. I deinstalled that first and now everything works out ok.

---

### Post by AlexsAntidote on 2009-08-05
I tried removing kompozer, but it failed. I tried purging and that failed too.

```
alex@notebook:~$ sudo apt-get remove kompozer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libnspr4-dev but it is not going to be installed
  kompozer-dev: Depends: kompozer (>= 1:0.7.10-0ubuntu6) but it is not going to be installed
  libnss3-dev: Depends: libnspr4-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alex@notebook:~$ sudo apt-get purge kompozer kompozer-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libnspr4-dev but it is not going to be installed
  libnss3-dev: Depends: libnspr4-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I'm stumped. I tried googling for issues with libnspr4 but can't find anything relevant.

---

### Post by AlexsAntidote on 2009-08-07
OK finally fixed it after some more messing around... In case anyone else has this problem here's what I had to do...

```

sudo apt-get remove kompozer kompozer-dev libnspr4-dev adobe-flashplugin libnss3-dev

sudo apt-get install libnspr4-dev
sudo apt-get install libnss3-dev adobe-flashplugin

```

I didn't install kompozer again since I don't really use it that much and I didn't want to have to deal with this problem again as it seems the problem had to do with Kompozer in the first place (though I could be wrong).

---

