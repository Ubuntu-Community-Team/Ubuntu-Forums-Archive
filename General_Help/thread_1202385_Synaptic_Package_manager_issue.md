---
title: "Synaptic Package manager issue"
date: 2009-07-02
forum: General Help
---

### Post by aidanandrach on 2009-07-02
Hey guys, pretty new to all this, so please be nice!

Tried to add OpenOffice and a few other bit and pieces the other night using Synaptic Package Manager.  It hung halfway through and I was forced to hard power down the system.

Attempted to run this again today, and received a message stating that "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So I ran the sudo command above and it then hangs at the first step - installing the openoffice package (mailmerge component I think).

So then, where to from here?!

Thanks in advance
Aidan

---

### Post by fooman on 2009-07-02
try these one at a time in a terminal:

```
sudo dpkg --configure -a
``````
sudo apt-get update
``````
sudo apt-get upgrade
```post back with any errors you see.

openoffice should already be installed.  if you want to upgrade to the latest,  try this:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

if its not installed (not sure as i just noticed your using ubuntu-studio)...add the appropriate repos as in the link i gave you above,  then run this command:

```
 sudo apt-get install openoffice.org
```

hope that helps.

---

### Post by aidanandrach on 2009-07-02
Thanks for the reply mate

```
sudo dpkg --configure -a
```

gives me

```
Setting up openoffice.org-emailmerge (1:3.0.1-9ubuntu3) ...
Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
```

No error messages - but it hangs there.  Left it running all night, no change.  Rest of the system becomes pretty much unresponsive.

I'll post this one, then try the others, just in case they crash the system too!

Back soon...

---

### Post by aidanandrach on 2009-07-02
```
sudo apt-get update
```

just runs through the update routine and finishes quite happily.

---

### Post by wojox on 2009-07-02
After you update then

```
sudo apt-get upgrade
```

---

### Post by aidanandrach on 2009-07-02
Thanks guys, 

```
sudo apt-get upgrade
```

hangs at the same point (mailmerge.py) as above.

Thoughts?

---

### Post by aidanandrach on 2009-07-03
So, any ideas on where I can start to clean this up folks?
 
Thanks in advance.
Aidan

---

### Post by aidanandrach on 2009-07-04
Very keen to get this one sorted out - any ideas on why the update for mailmerge.py is causing the system to hang?  Is there anythign I can do to clear this out of the update?

Cheers in advance.

---

### Post by michy99 on 2009-07-04
What is the output from```
ls /var/cache/apt
```

---

### Post by aidanandrach on 2009-07-05
> **michy99 said:**
> What is the output from```
ls /var/cache/apt
```

Thanks Michy, gives me 

```
archives  pkgcache.bin  srcpkgcache.bin
```

Thoughts?

---

### Post by michy99 on 2009-07-05
Sorry, I messed up. What is the output of```
ls /var/cache/apt/archives
```

---

