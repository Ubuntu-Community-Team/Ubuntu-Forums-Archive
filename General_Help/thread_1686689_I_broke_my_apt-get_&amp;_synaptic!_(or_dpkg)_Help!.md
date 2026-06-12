---
title: "I broke my apt-get &amp; synaptic! (or dpkg?) Help! &quot;package `gpgv': Input/output error"
date: 2011-02-12
forum: General Help
---

### Post by indstr on 2011-02-12
I've really screwed it up this time...

I'm currently running Ubuntu Studio 9.10 which I plan on upgrading after the month of February is over (working on the "rpm challenge" and I don't want to have to spend hours configuring an upgrade until after the month is over) ... 

However I tried installing Jack 1.9.6 from a PPA repository. Had some trouble with it so I tried uninstalling it by using ppa-purge to revert back to my previous version of jack. I also ended up reinstalling alsa in the process. 

Everything's fine, except for the fact that I cannot get apt-get or synaptic to do anything!

They always give the same error, pretty much regardless of what I try to do (add/remove/upgrade). The error is:

```
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `gpgv': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```This is regardless of whether I do it at the terminal with apt-get or in synaptic. 

I've tried reinstalling gpgv, dpkg, etc... Of course it gives me the same error every time.  

I've tried:

```
sudo dpkg --configure -a
``````
sudo apt-get -f install
``````
sudo dpkg-reconfigure --force gpgv
``````
sudo dpkg-reconfigure -a
```None of those work.

I've tried running the update manager. It says I need to run a partial upgrade. Fine, I clicked it but it fails and gives me an error saying it can't authenticate certain packages. 

I'm completely at a loss for what to do. Is this some kind of corrupted-file issue? How can I fix it? Any help would be appreciated

:confused::confused::confused:

---

### Post by Habeouscorpus on 2011-02-12
```
sudo apt-get upgrade 
```

might work. Say yes to the unauthenticated packages.

---

### Post by indstr on 2011-02-12
I gave it a try ... 

No go... 

It downloaded the packages and then:

```
Fetched 317MB in 6min 2s (875kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
debconf: Unknown template field '_description', in stanza #1 of /tmp/muse.template.100880

(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `gpgv': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Same error...

:confused:

---

### Post by Habeouscorpus on 2011-02-12
Oh. sudo apt-get update maybe?

Also, from [http://ubuntuforums.org/archive/index.php/t-89989.html](http://ubuntuforums.org/archive/index.php/t-89989.html)
> 
sudo rm -f *.deb /var/cache/apt/archives
sudo apt-get update
sudo rm -f /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/partial/lock
sudo apt-get clean

These commands might help you. Do them in order. (BE VERY CAREFUL TYPING. They will delete stuff, but don't let it delete stuff you want.)


Also, boot to a live disk and do a fsck if this doesn't work.

---

