---
title: "Will menu problems go away with dist-upgrade"
date: 2011-08-18
forum: General Help
---

### Post by choclo on 2011-08-18
Hello there, i foolishly upgraded 9.1 with some experimental debian stuff there and now the menus are all screwed up. There's not clock, show desktop, notification area and other such applets. The gnome dependencies have been compromised. It says something about the python_gmenu (=2.28.0.1-0ubuntu1) but 3.0.1-1 is already installed.
E: Unmet dependencies try using -f.

Now I was going to upgrade my distribution to 10.04 seeing as 9.1 is not supported anymore and I wanted to play Quake 1 and was wondering would these problems still exist if I did or have i totally screwed up my ubuntu.

I have since taken away the line in /etc/apt/sources.list which caused me to mess this up in the first place.

Please help good lads and lassies
the choc

---

### Post by seawolf167 on 2011-08-18
> **choclo said:**
> i foolishly upgraded 9.1 with some experimental debian stuff

I highly doubt they will go away or be fixed with any subsequent updates/upgrades. IMO you have two choices

[LIST=1]
[*]Reinstall
[*]Remove all Gnome config files using the below command
[/LIST]
 The second one will reset your desktop to the way it were as if you had  just done a fresh install. Before you decide to go this route - see if  any other packages are broken or not working due to version mismatches  from the dist-upgrade. Be very careful typing in the below command if you go this route. It will delete **ALL YOUR CONFIGURATION FILES**.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```Then log out and back in again.

---

### Post by CatKiller on 2011-08-18
You can probably force the version of that package to the Ubuntu version. Synaptic may then be able to sort out the dependencies. Otherwise, I seem to recall that there's an option to show where the packages came from. You might be able to use that to sort out your version problems. A re-install may be quicker, but I think it's doable. Assuming that all the packages from the updated version are newer than the Debian versions you've installed, a dist-upgrade might help, or it might make it worse. Prepare for a re-install anyway, just in case.

---

### Post by choclo on 2011-08-18
"reset your desktop to the way it were as if you had just done a fresh install" - that means it'll work properly though right? 

What if I do that and then dist-upgrade?

Thanks for the replies guys

---

### Post by seawolf167 on 2011-08-18
> **choclo said:**
> "reset your desktop to the way it were as if you had just done a fresh install" - that means it'll work properly though right?

It should, yes. Although having experimental Debian binaries and packages on your system may mean that there are other unresolved or conflicts that exist beyond the scope of Gnome 2. If you can make a backup with [Clonezilla]("http://www.clonezilla.org") before hand you have a way out if it doesn't help (or god forbids makes anything worse).

---

