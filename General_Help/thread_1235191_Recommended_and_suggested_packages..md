---
title: "Recommended and suggested packages."
date: 2009-08-08
forum: General Help
---

### Post by user 123 on 2009-08-08
What is the difference between recommended and suggested packages and which are automatically installed when installing other packages with apt-get and synaptic? If they are is there any way to stop them being installed so I don't install unneeded packages?
Thanks.

---

### Post by drs305 on 2009-08-08
You can avoid recommended packages from being included in an install in Synaptic via Settings, Preferences, General tab: Untick "Consider recommended packages as dependencies".

With apt-get, you can include the switch "--no-install-recommends".

Dependencies must be present to run the package. I can't tell you what specifically qualifies a package as a recommended one other than what the adjective suggests.

A CLI method of displaying dependencies and suggests is: [COLOR="DarkRed"]apt-cache show <packagename>[/COLOR]   
Example:  apt-cache show gimp

---

### Post by user 123 on 2009-08-09
> **drs305 said:**
> You can avoid recommended packages from being included in an install in Synaptic via Settings, Preferences, General tab: Untick "Consider recommended packages as dependencies".

With apt-get, you can include the switch "--no-install-recommends".

Dependencies must be present to run the package. I can't tell you what specifically qualifies a package as a recommended one other than what the adjective suggests.

A CLI method of displaying dependencies and suggests is: [COLOR="DarkRed"]apt-cache show <packagename>[/COLOR]   
Example:  apt-cache show gimp


Thanks for this.
Is there any chance you could show me and example of the usage of --no-install-recommends?
Would it be for example:
apt-get install --no-install-recommends firefox?

Also is there any way to make this permanent so that i do not have to enter this command every time I install something?

---

### Post by drs305 on 2009-08-09
> **user 123 said:**
> Thanks for this.
Is there any chance you could show me and example of the usage of --no-install-recommends?
Would it be for example:
apt-get install --no-install-recommends firefox?


I found a package called *cuetools*, which has a suggested/recommends of *flac*. We can see this by running "apt-cache show cuetools", which displays, in part:
> Recommends: flac (>= 1.1.3)

If we run the install command normally, we get (in part):
> 
**sudo apt-get install cuetools**
The following NEW packages will be installed:
  [COLOR="DarkRed"]cuetools flac[/COLOR]

If we run the command with the switch, the result changes to:
> 
**sudo apt-get install --no-install-recommends cuetools**
The following NEW packages will be installed:
  [COLOR="DarkRed"]cuetools[/COLOR]


Now to the more important part: *should* you do this. Aptitude, apt-get and Synaptic in releases 8.10 (Intrepid) and later have dependencies enabled by default. Synaptic does *not* have the recommends enabled by default in Hardy. The developers have moved toward including the recommends in an install. If I were to decide not to install the recommends, I would only do it on a case by case basis and not generally. But they are *not* required, so the decision is up to you.

> Also is there any way to make this permanent so that i do not have to enter this command every time I install something?

If you wanted to make the default action of apt-get or aptitude to omit recommends, you could create an alias such as "aptgetnone" and include the switch, which would override the default action to install the additional packages. You could use the actual command name for the alias but would then have to override the alias whenever you wanted to install the recommends.

---

### Post by limestone on 2010-10-19
> **user 123 said:**
> 
apt-get install --no-install-recommends firefox?

You can do it with -R also.
sudo aptitude install -R firefox (install without recommends)

and if you have chosen to avoid recommended from the settings and would like to install them on some package use -r.
sudo aptitude install -r firefox (install with recommends)

---

