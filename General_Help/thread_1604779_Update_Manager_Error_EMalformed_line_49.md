---
title: "Update Manager Error: E:Malformed line 49"
date: 2010-10-24
forum: General Help
---

### Post by SkiBarn on 2010-10-24
For some reason my Update Manager will not run.  

This is what comes up:

E:Malformed line 49 in source list/etc/apt/source.list (dist parse), E. The list of sources could not be read.

I am at the point of rebooting and reloading the OS.  Any help is appreciated.

Thanks!

PS Oh and for some reason the Ubuntu Software Center is not bringing up the lists of Office, Games, Graphics, Sound and Video, etc.  I don't know if the 2 are related.

---

### Post by TeoBigusGeekus on 2010-10-24
```
gksu gedit /etc/apt/source.list
```
Post us the contents of the file.

---

### Post by Elfy on 2010-10-24
You have a problem with line 49 - the sources list should only have lines starting with #, deb or deb-src. Anything else will cause errors.

If you are not sure then open the file with gedit and paste it here. If you are sure open it as root to edit.

```
gksudo gedit /etc/apt/source.list
```

---

### Post by howefield on 2010-10-24
> **TeoBigusGeekus said:**
> ```
gksu gedit /etc/apt/source.list
```
Post us the contents of the file.

Or even...

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by TeoBigusGeekus on 2010-10-24
^^^^^^^^^^^ This.

---

### Post by Elfy on 2010-10-24
:lol:

Looks like a bunch of us all hanging about looking for something to do :)

Personally I'd rather sudo nano -B /etc/apt/sources.list

---

### Post by SkiBarn on 2010-10-24
When I go to run the Update Manager (which there is a red circle with a white bar in the middle in the upper right of the screen) this is what comes up:[INDENT]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 49 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

[/INDENT]I tried the gedit code and nothing comes up in the source list.

---

### Post by howefield on 2010-10-24
> **SkiBarn said:**
> I tried the gedit code and nothing comes up in the source list.

Did you try

```
gksudo gedit /etc/apt/sources.list
```

as /etc/apt/source.list most likely doesn't exist so no surprise that it would come up empty.

---

### Post by SkiBarn on 2010-10-24
Here it is:

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/karmic](http://archive.canonical.com/karmic) partner
deb [http://us.archive.canonical.com/](http://us.archive.canonical.com/) lucid partner

---

### Post by howefield on 2010-10-24
Put a # sign in front of the second to last line and save the file.

# deb [http://archive.canonical.com/karmic](http://archive.canonical.com/karmic) partner

Then try again.

---

### Post by SkiBarn on 2010-10-24
That was the winner!  Thanks Again!

That also fixed the Ubuntu Software Center (the programs are now viewable).

---

### Post by howefield on 2010-10-24
> **SkiBarn said:**
> That was the winner!  Thanks Again!

Weyhey.. another lucky guess ;-)

Glad you're sorted.

---

### Post by Throne777 on 2011-03-21
Getting the same error but with line 61. 

Sources list is:
```

# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

Do I just # the 61st line (what counts as the 61st line? Are spaces included?)? If so, what will no longer be part of the list (is it one that you really need part of the list?)?

---

### Post by oldos2er on 2011-03-21
Mixing repositories from different distributions is asking for trouble. I recommend you remove both 'lucid partner' repos from your sources.list. After you make these changes, run **sudo apt-get update**

---

### Post by Throne777 on 2011-03-21
> **oldos2er said:**
> Mixing repositories from different distributions is asking for trouble. I recommend you remove both 'lucid partner' repos from your sources.list. After you make these changes, run **sudo apt-get update**

Oh yeah, well spotted. Thanks for that :)

---

