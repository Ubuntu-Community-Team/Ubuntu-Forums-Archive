---
title: "apt-get update errors"
date: 2009-10-06
forum: General Help
---

### Post by rifak on 2009-10-06
hey,
i've been using ubuntu for a while now, and this just started happening...whenever i run "sudo apt-get update" it fails on every source repo. are they doing updates to the repos or something? or is it something corrupt within my files...?

here's the errors it spits out:

```
Err http://winff.org hardy Release.gpg                                                
  Could not resolve 'winff.org'
Err http://winff.org hardy/universe Translation-en_US                                 
  Could not resolve 'winff.org'
Err http://debian.o-hand.com hardy/ Release.gpg                                       
  Could not resolve 'debian.o-hand.com'
Err http://debian.o-hand.com hardy/ Translation-en_US                                 
  Could not resolve 'debian.o-hand.com'
Fetched 3389B in 40s (85B/s)                                                          
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

```

and more of the same...a really huge list of all errors

---

### Post by paul.gevers on 2009-10-06
> **ego-sum-deus said:**
> hey,
i've been using ubuntu for a while now, and this just started happening...whenever i run "sudo apt-get update" it fails on every source repo. are they doing updates to the repos or something?
To the last answer, no.

> **ego-sum-deus said:**
> or is it something corrupt within my files...?

here's the errors it spits out:

```
Err http://winff.org hardy Release.gpg                                                
  Could not resolve 'winff.org'
Err http://winff.org hardy/universe Translation-en_US                                 
  Could not resolve 'winff.org'
Err http://debian.o-hand.com hardy/ Release.gpg                                       
  Could not resolve 'debian.o-hand.com'
Err http://debian.o-hand.com hardy/ Translation-en_US                                 
  Could not resolve 'debian.o-hand.com'
Fetched 3389B in 40s (85B/s)                                                          
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

```

and more of the same...a really huge list of all errors

It looks like your domain resolving is buggy at the moment. But apparently you are still connected to the internet? I would try (I know, M$ Windows solution) to restart your computer.

You can test if everything is ok, by running ```
host winff.org
``` or ```
host us.archive.ubuntu.com
```in a terminal.

---

### Post by rifak on 2009-10-06
> **paul.gevers said:**
> To the last answer, no.



It looks like your domain resolving is buggy at the moment. But apparently you are still connected to the internet? I would try (I know, M$ Windows solution) to restart your computer.

You can test if everything is ok, by running ```
host winff.org
``` or ```
host us.archive.ubuntu.com
```in a terminal.

when i run the host command everything comes back fine..no errors. and i've already tried restarting and shutting down. is there a way to reconfigure your sources.list or apt keys?

---

### Post by paul.gevers on 2009-10-06
> **ego-sum-deus said:**
> when i run the host command everything comes back fine..no errors. and i've already tried restarting and shutting down. is there a way to reconfigure your sources.list or apt keys?

Yes there is a way to reconfigure the sources.list, but the problem is NOT there. The error clearly says > Could not resolve 'winff.org' and > Could not resolve 'debian.o-hand.com'. As both do exist this means a problem with apt and resolving: ```

paul@elbrus ~ $ host debian.o-hand.com
debian.o-hand.com has address 80.68.88.162
paul@elbrus ~ $ host winff.org
winff.org has address 131.155.114.222

```

But anyway the sources.list is found in /etc/apt/ The winff.org repo might be located in /etc/apt/sources.list.d/winff.list You must have root privileges to edit these files, or even better, try editing them with your favorite package manager (synaptic?).

The way to edit your keys is again with your favorite package manager or with apt-key. See the man page ```
man apt-key
```

---

### Post by rifak on 2009-10-06
ok, so the problem isn't anything to do with keys or sources. i am here on my schools network, and everything updated and downloaded/installed fine...no errors. 

so, what could be causing this problem at home? network issues?..i have no idea. everything was been working fine until last week. it just started doing this. oh, and also, when i open pidgin, my gmail and yahoo names will sign-on fine, but my AIM name will sometimes load the first time, or i will have to close out, and then reopen pidgin and then the AIM name will log on...maybe related?

---

### Post by sir_cheats_a_lot on 2009-10-06
I would say it'd have to do with your previous network.  though it is rather odd that it'd work fine one week and not the next.  maybe it was something you installed/reconfigured recently?    

The pidgin thing isn't likely to be related.  the version in the Hardy repo is rather buggy and has been for the last couple "Hardy" versions.  maintainers of the repo wont do anything about upgrading it until something security related though.  version in the repo: v 2.5.2.  current version: 2.6.2.   it would be nice if they at least had an updated version of the facebook plugin. the one i've got is constantly getting disconnected *grumbles*. haven't tried the newest version of it because it requires the newest version of pidgin. :( .

---

