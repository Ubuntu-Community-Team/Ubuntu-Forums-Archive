---
title: "723 broken packages, 820 installed"
date: 2011-07-05
forum: General Help
---

### Post by h0t1ce on 2011-07-05
Hi,

This morning I noticed that update-manager had an error message stating I had packages with unmet dependencies. The funny thing is I haven't installed anything during the night (auto-update maybe?)

I go in synaptic and it says I have 723 broken packages with 820 installed. I tried rebooting but that doesn't fix the problem. The good news is that my system works even after the reboot.

Trying to let synaptic fix this would make it remove all the packages. So what would be the way to go to get this fixed gracefully?

thanks in advance!

---

### Post by dino99 on 2011-07-05
clean the cache: clean, autoclean, autoremove
deactivate non genuine repo (ppa)

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(can take some time, dont stop it)

---

### Post by hawthornso23 on 2011-07-05
I don't believe you have this many broken packages. I suspect your package information is corrupted. Get update manager to check for updates. That should refresh the package database. Try that first.

---

### Post by h0t1ce on 2011-07-05
Thanks for the quick reply dino99!

I followed your advice including removing unofficial repositories and ppa's.

All commands went well except autoremove and install -f

at autoremove there was a ton of dependencies that were unmet (seems Im missing a lot of essential files (such as libc6 for example) So the autoremove ends with 
```
E: Unmet dependencies. Try using -f.
```

Should I go ahead and do autoremove with the f flag?


then install -f gives me this, I presume it's because autoremove didnt get to do it's job.
```
The following packages have unmet dependencies:
 php5-gd : Depends: phpapi-20090626+lfs
E: Internal Error; autoremove broke something

```

thanks

---

### Post by dino99 on 2011-07-05
run :

sudo rm /var/cache/apt/archives/*
(dont woory about the warning)

then update again

note: if troubles persist, maybe you need to downgrade some conflicting package(s) via synaptic if actual version is from a ppa or extra source.

you can also remove/purge then reinstall the conflicting package(s)

---

### Post by h0t1ce on 2011-07-05
> **hawthornso23 said:**
> I don't believe you have this many broken packages. I suspect your package information is corrupted. Get update manager to check for updates. That should refresh the package database. Try that first.

I tried letting update-manager 'look at it' but it said it wouldn't do any updates until the unmet dependencies were fixed.

---

### Post by h0t1ce on 2011-07-05
dino I tried 
```
sudo rm /var/cache/apt/archives/*
```
 then I update followed by install -f.
I get the same error:
```
 The following packages have unmet dependencies:
 php5-gd : Depends: phpapi-20090626+lfs
E: Internal Error; autoremove broke something
```

---

### Post by h0t1ce on 2011-07-05
dino,

I'd be willing to purge an reinstall,

any safe way to do it? a command to say to purge yet reinstall after? Or do I have to reinstall ubuntu-desktop and every other extra packages I had installed by hand?

thanks for you time

---

### Post by hawthornso23 on 2011-07-05
I wasn't suggesting to actually try to update anything, just click on the 'check' button in the update manager. It does the same thing as 

```
apt-get update
```

When your system tells you suddenly out of the blue that you have 720 broken packages then you probably don't. What you most likely have is a corrupted package database. 

So update your package information and see if that fixes the problem. 

However it looks like you've gone beyond that point now.

---

### Post by dino99 on 2011-07-05
as i can see, its php5* packages that warns, so look at possible downgrade via synaptic, or purge them and reinstall, no need to to do a fresh install (albeit its a good idea if the system is borked, sometimes its quicker)

An other check: be sure you dont mix distro into /etc/sources.list

---

### Post by h0t1ce on 2011-07-05
Ok now for some reason right-clicking on php5-gd in synaptic and choosing fix makes it downgrade php5-gd and another php5 file and updates/reinstalls my other 700's of broken packages instead of suggesting to remove all broken packages. Since the packages weren't cached anymore it's going to take a while but I think this problem will be solved.

I'll let you know. thanks

---

### Post by h0t1ce on 2011-07-05
Actually, it's not looking good

```
Extracting templates from packages: 100%
Preconfiguring packages ...
[wordlist,dc_debconf_select] error: [american (American English)] does not correspond to any package
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error
```

I guess I'll go reinstall my system :(

---

