---
title: "Cannot open Repositories, Software sources or Ubuntu Software Center"
date: 2010-11-05
forum: General Help
---

### Post by Jetro on 2010-11-05
I have already posted in a dozen different topics, but I don't want to hijack them, as some of them have different errors and problematiques than I have.

Nothing happens when trying to open Repositories. At the beginning, I was asked to reload, and I checked "do not repeat this message" (or something, I can't quite rephrase it), and so I tried again, nothing happens.

When clicking Ubuntu Software Center, I see a taskbar "window" for "Starting Administrative..." which then disappears.

When clicking Software Sources, I am asked for my password, then nothing.


Update manager works normally.

I am running Ubuntu 10.04

Here are some commands I've been adviced to try and the error messages I get:


```
gksu /usr/bin/software-properties-gtk

    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```


```
Software-Center

Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 22, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 88, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint
```

For the record, I do not have Linux Mint installed, except for a Mint menu, so I could have it on my Gnome panel.

:(

---

### Post by CharlesA on 2010-11-05
Can you post the contents of /etc/apt/sources.list inside [noparse]```

```[/noparse] tags.

---

### Post by Jetro on 2010-11-05
Here it is:
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://no.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid universe
deb http://no.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://no.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by CharlesA on 2010-11-05
It looks ok.

Are there anything listed in /etc/apt/sources.list.d/ ?

---

### Post by Jetro on 2010-11-05
*sources.list.d* is a folder.

It contains these files:

file:///etc/apt/sources.list.d/gnomenu-team-ppa-lucid.list
```
deb http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu lucid main
```

file:///etc/apt/sources.list.d/gnomenu-team-ppa-lucid.list.save
```
deb http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu lucid main
```

file:///etc/apt/sources.list.d/opera.list
```
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
```

file:///etc/apt/sources.list.d/opera.list.save
```
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
```

file:///etc/apt/sources.list.d/ubuntu-tweak-stable.list
```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu lucid main #Ubuntu Tweak Stable Source
```

file:///etc/apt/sources.list.d/ubuntu-tweak-stable.list.save
```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu lucid main #Ubuntu Tweak Stable Source
```

---

### Post by CharlesA on 2010-11-05
Does this return any errors?

```
sudo apt-get update
```

---

### Post by Jetro on 2010-11-05
Nope! I get a bunch of hits, a  few Ign's, and the last thing it says is "Reading package lists... Done."

These are the Ign's:
```
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US  
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                  
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://deb.opera.com stable/non-free Packages
Ign http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US

```

---

### Post by Jetro on 2010-11-09
Sorry to bump, but this is an extremely annoying issue. For instance, I cannot upgrade to Ubuntu 10.10, which I would like. :(

---

### Post by CharlesA on 2010-11-09
The apt-get update looked fine.

When you say that you can't upgrade to 10.10, is it set to LTS only in update manage properties?

---

### Post by mc4man on 2010-11-09
It would seem more than likely that your mint menu and or whatever you did to install/use is behind your current troubles.
Maybe try to remove/revert any changes you made.

I can't see it being of any use as is in regards to an upgrade to 10.10.

Of some interest - exact same error message for sc

[http://forums.linuxmint.com/viewtopic.php?f=47&t=50405](http://forums.linuxmint.com/viewtopic.php?f=47&t=50405)

This poster (who is actually using mint), solved his issue by editing /usr/share/software-center/softwarecenter/distro/_init_.py, not sure the value to you.
[http://jeffhoogland.blogspot.com/2010/06/howto-use-ubuntu-software-center-in.html](http://jeffhoogland.blogspot.com/2010/06/howto-use-ubuntu-software-center-in.html)

---

### Post by Jetro on 2010-11-09
CharlesA: Yes, I suppose so. Update manager works - as far as I know - normally and I haven't been prompted to upgrade, so it's probably only set to LTS releases.

mc4man: I removed all the mint packages (which I also have done before, to no effect), but still got the same error message. Thanks to the links you provided, though, Ubuntu Software Center is now working. Thanks.

However, I still cannot access either Software Sources or Repositories. Any commands I should run to diagnose the problem here?

---

### Post by mc4man on 2010-11-10
Run this - maybe something will show up
```
sudo software-properties-gtk --debug
```

or 
```
sudo software-properties-gtk -m
```

Edit: if you were to browse to /etc/apt and d.left click on sources.list - what happens (default should be to open in software sources

---

### Post by Jetro on 2010-11-10
I get the same kind of error on both commands (exactly the same):
```
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 113, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```

> **mc4man said:**
> browse to /etc/apt and d.left click on sources.list - what happens
Nothing. When I right-click it, the default alternative is indeed to open it with Software Sources.

Also, I replaced the SoftwareProperties.py file, to no change. I also reinstalled python. Exact same error message.

---

### Post by Jetro on 2010-11-15
Anyone got any ideas?

I've searched the error message in question, but it hasn't returned any answers relevant to my problem... :(

---

### Post by Jetro on 2010-11-23
Here's my /etc/lsb-release file:
```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=9
DISTRIB_CODENAME=isadora
DISTRIB_DESCRIPTION="Linux Mint 9 Isadora"
```
I don't get why it says that. It may have to do with fixing the Ubuntu Software Center bug I got fixed earlier.

I changed it to
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu Lucid Lynx"
```

...and now it works! :D That is, both Software Sources and Repositories. (Even though those are the same.(?))

Ubuntu Software Center also works after this change. ;)

---

