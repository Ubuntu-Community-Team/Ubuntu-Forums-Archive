---
title: "how to fix source list?"
date: 2012-01-19
forum: General Help
---

### Post by georgekyr on 2012-01-19
i tried to open update manager but it returned this error:'E:Type 'sudo' is not known on line 63 in source list /etc/apt/sources.list'

how can i fix this?

---

### Post by snowpine on 2012-01-19
Let's start from the beginning... do you know how to edit a text file? Since the file is outside your /home folder, you'll need to use 'sudo' (for a terminal text editor) or 'gksu' (for a GUI editor). Let's use gedit for the sake of argument:

```
gksu gedit /etc/apt/sources.list
```

The short answer to your question is, whatever you did to line 63 of this file, you did it wrong ("sudo" has no place in this file), so undo the change you made. :)

A longer answer is, post the contents of the file so we can take a look (be sure to use code tags for legibility):

```
cat /etc/apt/sources.list
```

---

### Post by cogier on 2012-01-19
Go to the **Software Centre** and on the **Edit** menu select **Software Sources**, enter your password when requested. Select the **Other Software**tab.

You should be able to see what the issue is.

---

### Post by georgekyr on 2012-01-19
> **snowpine said:**
> Let's start from the beginning... do you know how to edit a text file? Since the file is outside your /home folder, you'll need to use 'sudo' (for a terminal text editor) or 'gksu' (for a GUI editor). Let's use gedit for the sake of argument:

```
gksu gedit /etc/apt/sources.list
```

The short answer to your question is, whatever you did to line 63 of this file, you did it wrong ("sudo" has no place in this file), so undo the change you made. :)

A longer answer is, post the contents of the file so we can take a look (be sure to use code tags for legibility):

```
cat /etc/apt/sources.list
```
i'm a newbie on linux (:
here are the contents of the file:
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main


sudo apt-get update

---

### Post by snowpine on 2012-01-19
Deleting this line, saving the file, and running Update Manager again should solve your problem:

```
sudo apt-get update
```

It looks like you made this error when you were adding Ubuntuzilla to this file. Remember that sources.list is an important system file; one small typo and you won't be able to update or install apps (as you've discovered). So in the future, be very careful, follow only trusted how-to's, and use copy & paste to avoid errors. Better yet, you can use the graphical Software Sources application so you don't have to edit this file directly. :)

---

### Post by georgekyr on 2012-01-19
i tried to install thunderbird 9.0.1 i downloaded from firefox. then i got the error.

---

### Post by snowpine on 2012-01-19
Did deleting line 63 fix the problem and allow you to install Thunderbird? If so, hooray, you can mark your thread Solved. :)

---

### Post by georgekyr on 2012-01-19
it seems like the problem is fixed! thank you!:-D

---

