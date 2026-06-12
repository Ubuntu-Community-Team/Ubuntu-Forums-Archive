---
title: "Update error - does it mean?"
date: 2010-07-07
forum: General Help
---

### Post by JEBB on 2010-07-07
When running Update Manager today it returned this error message:  
W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.5+build2+nobinonly-0ubuntu0.10.04.1_i386.deb](http://archive.linux.duke.edu/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.5+build2+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found 

What does it mean? what should I do about it?  

Thanks.

---

### Post by hansdown on 2010-07-07
Hi JEBB.

Which version of ubuntu are you using?

---

### Post by JEBB on 2010-07-07
"Which version of ubuntu are you using?"

I'm running UNR 10.04.

---

### Post by hansdown on 2010-07-07
Sorry for asking that. I just saw your sig.

That link is indeed, dead.

Is your sources list up to date?

Is this an upgrade?

Try

```
sudo nano /etc/apt/sources.list
```

Hope this helps.

---

### Post by JEBB on 2010-07-07
"Sorry for asking that. I just saw your sig.
That link is indeed, dead.
Is your sources list up to date?
Is this an upgrade?

Try
Code:

sudo nano /etc/apt/sources.list"

This is what that returned:

# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) lucid multiverse

---

### Post by JEBB on 2010-07-07
Should I just delete Thunderbird?

---

### Post by hansdown on 2010-07-07
Please bear with me, Im not that geeky.

Click system> administration> software sources.

Is the part, that says

```
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted

```
Checked?

If so, uncheck it.

You may need to install

```
ubuntu restricted extras
```

from synaptic.

---

### Post by plucky on 2010-07-08
The problem is the file it is looking for on the repository does not exist
```
/thunderbird_3.0.5+build2+nobinonly-0ubuntu0.10.04.1_i386.deb
```

But what is on the repository is ```
/thunderbird_3.0.5+build2+nobinonly-0ubuntu0_i386.deb
``` so something has got out of step with the package lists.

I would give it a day or so to allow the repository to catch up and then try again,or switch your repository to the "Main Server" to see if the problem goes away.

To switch repositories,open Software Sources and select from the Download Server dropbox.

Good Luck

---

### Post by JEBB on 2010-07-08
Plucky hit it!

This morning's updates included an update to Thunderbird and no error message resulted.  All is well.

---

