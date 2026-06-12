---
title: "Different packages in apt-get vs. Synaptic"
date: 2009-08-02
forum: General Help
---

### Post by bdentremont on 2009-08-02
I have been trying to figure out why apt-get can summon packages that don't seem to exist via Synaptic.  This has been puzzling me for some time.  For example, I am now running Ubuntu 9.04 and trying to install Skype.  I understand this to be in the Mediubuntu repository and thus I added this repository (URI: *[http://packages.medibuntu.org/](http://packages.medibuntu.org/)*; Distribution: *jaunty*; Components: *free non-free*) and the associated gpg key at the software sources dialog.  I also enabled all four software classes (main, universe, universe, and multiverse) did a reload in Synaptic.  Now, if I search for "skype" in Synaptic, I get one relevant result, *skype-mid*.  However, if I issue *sudo apt-get install skype*, apt-get proposes installing the packages *skype* and *skype-common*.  Aptitude is aware of these two packages as well, but I can't find them in Synaptic.  I have had similar experience in the past, I believe always with non-free packages.

I find stuff telling me that Synaptic is a GUI alternative to apt-get and aptitude, but for me they seem to yield different results.  Any thoughts would be appreciated.  Thanks.

---

### Post by cmost on 2009-08-02
Synaptic is merely a GUI to manage your packages, but, it does have some filtering ability which I suspect is the reason you see only a subset of packages to which you can actually access.  Go into Synaptic's Settings --> Preferences --> Distribution and tick the box next to "Always prefer highest Version".  Then, click apply and close the preferences dialog.  Click the 'Reload' button and then search for packages you know to be present in Mediabuntu.  See if that solves your issue.

---

### Post by michy99 on 2009-08-02
I find the Quick Search in Synaptic to be less than satisfactory. For best results, always use the regular Search function.

---

### Post by t0p on 2009-08-02
I think cmost might have it there.  I can see the various skype packages in Synaptic, and I have the settings cmost suggests.

---

### Post by mc4man on 2009-08-02
There was/is..? an issue where synatic isn't updated correctly after adding a repo (will within a week from cron.weekly

Running this resolves till the issue is fixed (if not already, I use hardy where it's not a problem

```
sudo update-apt-xapian-index
```

---

### Post by bdentremont on 2009-08-12
Thanks very much guys!  As an installed package, Skype always comes up in any search, but I think my primary problem may have been overuse of the quick search field.  I guess it never occurred to me that it wouldn't pull up a package by the exact name.

---

### Post by jocko on 2009-08-12
> **bdentremont said:**
> Thanks very much guys!  As an installed package, Skype always comes up in any search, but I think my primary problem may have been overuse of the quick search field.  I guess it never occurred to me that it wouldn't pull up a package by the exact name.
The "Quick Search" field does not search through the sources, it just removes the packages that does not match from the list you are currently showing.
So if you highlight "installed" in the list to the left in synaptic and then quick search for skype, it will only find the packages that are already installed. If you use the real search function you'll search through all the sources and show all packages that match the search, irregardless of what you had listed before.

---

