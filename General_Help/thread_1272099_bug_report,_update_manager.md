---
title: "bug report, update manager"
date: 2009-09-21
forum: General Help
---

### Post by rwarwarwa on 2009-09-21
Hi there,

When I opened update manager I got this...

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'" 

What is my next step?

Thanks,

rwa

---

### Post by sethhikari on 2009-09-21
In the command line can you still run

```
Sudo apt-get update
Sudo apt-get upgrade
```

---

### Post by wojox on 2009-09-21
Paste /etc/apt/sources.list up here and let's see.

---

### Post by snowpine on 2009-09-21
It's not a bug. You broke your /etc/apt/sources.list.

Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by rwarwarwa on 2009-09-21
file:///home/nev/Desktop/sourceslist.txt


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://mirror.noreply.org/pub/tor/jaunty](http://mirror.noreply.org/pub/tor/jaunty) main

---

### Post by snowpine on 2009-09-21
The error message tells you the problem is with line 54:

```
deb http://mirror.noreply.org/pub/tor/jaunty main
```

So edit the file (assuming you are using Ubuntu and the gedit text editor):

```
gksu gedit /etc/apt/sources.list
```

and comment out line 54 by typing a # symbol at the start of the line:

```
# deb http://mirror.noreply.org/pub/tor/jaunty main
```

Now try to update again.

At your leisure, do some more research about tor and how you installed it wrong. I have never used tor before so I can't help you with that...

---

### Post by rwarwarwa on 2009-09-22
Hi there, 

I get to the line put in a # in front of deb-http://mirror.noreply.org/pub/tor/jaunty main

I then went to a new terminal and typed in sudo apt-get update
I get
"E:Malformed line 54 is source list /etc/apt/sources.list (dist parse)"

I had to use sudo nano as gksu gedit was giving me GTK-warning**: cannot open display

I am using jaunty jakalope. 

What is the wrong thing?

thanks,

rwa

---

### Post by snowpine on 2009-09-22
Obvious question, but did you save your changes?

```
cat /etc/apt/sources.list
```

---

### Post by rwarwarwa on 2009-09-22
I guess not. I'll look into doing that. 

thanks,

rwa

---

### Post by rwarwarwa on 2009-09-23
Got it. Thanks for the lesson. 

rwa

---

