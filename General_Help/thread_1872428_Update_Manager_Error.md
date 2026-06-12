---
title: "Update Manager Error"
date: 2011-10-30
forum: General Help
---

### Post by scoobyd on 2011-10-30
Hi,

When I try to use the update manager, it gives me this error:

E:Malformed line 57 in source list /etc/apt/sources.list (dist parse)

How do I correct this?

Below is my /etc/apt/sources.list:

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.cim/natty](http://archive.canonical.cim/natty) partner
deb-src [http://archive.canonical.cim/natty](http://archive.canonical.cim/natty) partner
deb [http://archive.canonical.cim/natty](http://archive.canonical.cim/natty) partner
deb-src [http://archive.canonical.cim/natty](http://archive.canonical.cim/natty) partner
deb [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.com/oneric](http://archive.canonical.com/oneric) partner
deb-src [http://archive.canonical.com/oneric](http://archive.canonical.com/oneric) partner

---

### Post by Script Warlock on 2011-10-30
can you try this on your terminal

sudo apt-get install -f

---

### Post by scoobyd on 2011-10-30
This is what terminal churned out:

 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 83 not upgrade

But it doesn't fix the error message that the update manager shows

---

### Post by Script Warlock on 2011-10-30
sudo apt-get upgrade

---

### Post by scoobyd on 2011-10-30
sudo apt-get update

E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by Script Warlock on 2011-10-30
> Malformed line 57 are natty and oneiric can you try commenting those natty's and then try to update again,

---

### Post by PaulW2U on 2011-10-30
```
deb http://archive.canonical.[COLOR="Red"]**cim**[/COLOR]/natty partner
deb-src http://archive.canonical.[COLOR="red"]**cim**[/COLOR]/natty partner
```

Edit the file and replace .cim with .com.

---

### Post by Script Warlock on 2011-10-30
yeah what are those cim anyway

---

### Post by scoobyd on 2011-10-30
> **PaulW2U said:**
> ```
deb http://archive.canonical.[COLOR="Red"]**cim**[/COLOR]/natty partner
deb-src http://archive.canonical.[COLOR="red"]**cim**[/COLOR]/natty partner
```

Edit the file and replace .cim with .com.

Did that, saved the changes - error message still there


> **Script Warlock said:**
> are natty and oneiric can you try commenting those natty's and then try to update again,

How do I 'comment'?

---

### Post by Script Warlock on 2011-10-30
put a # before the deb [http://archive.cano](http://archive.cano)....

if not working try this

sudo rm /var/lib/apt/lists/* -vf

---

### Post by PaulW2U on 2011-10-30
You've missed out **ubuntu**, my sources.list contains:

```
deb http://archive.canonical.com/**ubuntu** oneiric partner
```

Sorry I didn't spot that in my last post.

---

### Post by scoobyd on 2011-10-30
> **PaulW2U said:**
> You've missed out **ubuntu**, my sources.list contains:

```
deb http://archive.canonical.com/**ubuntu** oneiric partner
```

Sorry I didn't spot that in my last post.

Added the ubuntu to that line and line below but it still gave me the line 57 error


> **Script Warlock said:**
> put a # before the deb [http://archive.cano](http://archive.cano)....

if not working try this

sudo rm /var/lib/apt/lists/* -vf

Commented line 57 to give:

E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Then did the same thing for all the natty to yield:

E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

Do I continue or try your sudo rm /var/lib/apt/lists/* -vf[ option?

---

### Post by Script Warlock on 2011-10-30
what are the lines 58 and 63 are they still natty? try commenting and see what else it displays.

---

### Post by scoobyd on 2011-10-30
58-62 are natty
63 is oneric



deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.cim/natty](http://archive.canonical.cim/natty) partner
deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneric partner

---

### Post by PaulW2U on 2011-10-30
Did you add **ubuntu** to the last two lines as well?

---

### Post by scoobyd on 2011-10-30
> **PaulW2U said:**
> Did you add **ubuntu** to the last two lines as well?

Yes I did.

---

### Post by Script Warlock on 2011-10-30
> **scoobyd said:**
> 58-62 are natty
63 is oneric



deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.cim/natty](http://archive.canonical.cim/natty) partner
deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb-src [http://archive.canonical.com/natty](http://archive.canonical.com/natty) partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneric partner

try commenting those

---

### Post by scoobyd on 2011-10-30
> **Script Warlock said:**
> try commenting those and if not try this 
sudo rm /var/lib/apt/lists/* -vf


Commenting all the natty in addition to adding the ubuntu to the last two lines fixed it. Wohoo!

Thanks so much guys! :D

---

