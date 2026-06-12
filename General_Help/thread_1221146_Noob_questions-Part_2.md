---
title: "Noob questions-Part 2"
date: 2009-07-23
forum: General Help
---

### Post by YasirMX on 2009-07-23
1) I've got the executable version of firefox and untared it, in which folder should I copy so as it forms part of the "installed programs on linux"??That is, I get it in the KDE Menu

2) I run firefox through a shell script that is "./firefox" but the terminal window shows up on every boot, how do I disable this?

---

### Post by Bucky Ball on 2009-07-23
Why don't you use Synaptics Package Manager? Much easier.

Think it's the same in Kubuntu:

System->Administration->Synaptic Package Manager

Then search for 'firefox' and install.


That or:

Applications->Add/Remove

... and search

---

### Post by philcamlin on 2009-07-23
> **bucky ball said:**
> why don't you use synaptics package manager? Much easier.
  +1

---

### Post by YasirMX on 2009-07-23
> **Bucky Ball said:**
> Why don't you use Synaptics Package Manager? Much easier.

Think it's the same in Kubuntu:

System->Administration->Synaptic Package Manager

Then search for 'firefox' and install.

The command line is much more fun, this is now a noob is promoted to "pro" :) please don't mind :)

---

### Post by Bucky Ball on 2009-07-23
sudo apt-get install firefox

... or something of the like. You probably need a version number there also.

---

### Post by YasirMX on 2009-07-23
> **Bucky Ball said:**
> sudo apt-get install firefox

... or something of the like. You probably need a version number there also.

I already have firefox, I mean to which directory should I copy the extracted folder??

---

### Post by SuperSonic4 on 2009-07-23
> **Bucky Ball said:**
> Why don't you use [s]Synaptics[/s] **KPackageKit's** Package Manager? Much easier.



Perhaps because the OP wants firefox 3.5 or a testing version?

I believe to make a program executable you need a copy in /usr/bin

(make a backup of mozilla's firefox in case it does not work)
```
sudo mv /usr/bin/firefox /usr/bin/firefox.bak
```

(make a symbolic link to wherever you've stored it. I've assumed it's in ~/firefox/)

```
sudo ln -s ~/firefox/firefox /usr/bin/firefox
```

Now try running firefox again, either from alt+f2 or KMenu. Beware you may need to reset plasma

Should you need to restore mozilla's firefox input the following command ```
sudo mv -v /usr/bin/firefox.bak /usr/bin/firefox
```

edit: I assume you made a choice to pick mozilla's firefox instead of the repo one? Should you want the repo one/not care you can get it with ```
sudo apt-get install firefox
```

---

### Post by Bucky Ball on 2009-07-23
> **SuperSonic4 said:**
> Perhaps because the OP wants firefox 3.5 or a testing version?

Totally true and I can see that now, my mistake, but it wasn't really made clear in the first post and I assumed because the OP had 9 posts they were trying to install firefox this way because they had no idea Synaptics even existed, perhaps ... :)

---

### Post by Zorael on 2009-07-23
> **Bucky Ball said:**
> Think it's the same in Kubuntu:

System->Administration->Synaptic Package Manager

Then search for 'firefox' and install.


That or:

Applications->Add/Remove

... and search
As for same in Kubuntu, very much no; Synaptic is a GNOME app, and hence not included in a normal Kubuntu installation. Installing it pulls a whole lot of dependency gunk we don't want. ;3

The KDE path would be *System Settings* > *Add and Remove Software* > search: firefox. Alternatively, run (alt+f2): **kpackagekit**. I'm not sure the add/remove software entry pops up in systemsettings unless you have the kdeadmin package installed, for instance.

But yeah, that'd net you the repo Firefox ~3.0.11* and not 3.5.

Another way would be to add the [Ubuntu Mozilla Daily](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) ppa and install the **firefox-3.5** package from there, but those are bleeding edge builds, so may prove buggy and crashy.

---

