---
title: "Update manager refuses to update"
date: 2011-08-15
forum: General Help
---

### Post by inga2 on 2011-08-15
I'm using [COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]Ubuntu 11.04 - the *Natty Narwhal* 
Update Manager shows me that there are 18 updates available for my system.
After  putting in my password, the updates appear to start, but then I get the  message that the updates would "Requires the installation of untrusted  packages" and just quits. 
The first update is for the Document  Viewer evince. It is from Ubuntu, yet the Update Manager claims it is an  "untrusted package."

HELP! [/COLOR][/FONT][/COLOR]

---

### Post by wojox on 2011-08-15
Open a terminal and run:

```
sudo apt-get update; sudo apt-get upgrade
```

Post back any errors.

---

### Post by inga2 on 2011-08-16
Well, that installed a whole bunch of updates in a  hurry. 

But why the original error?

Are there any settings I can change so that the updates work without going into the terminal?

I prefer the graphical way, partly because it gives me a choice re what to update, which the terminal did not.

---

### Post by wojox on 2011-08-18
> **inga2 said:**
> Well, that installed a whole bunch of updates in a  hurry. 

But why the original error?

Are there any settings I can change so that the updates work without going into the terminal?

I prefer the graphical way, partly because it gives me a choice re what to update, which the terminal did not.

Don't know. Are you using Evince installed from a ppa?

---

### Post by inga2 on 2011-08-24
I didn't install Evince separately. It came with the Ubuntu package.

But pardon my ignorance, what is "ppa"?

---

### Post by dschlesak on 2012-05-10
Personal Package Archives (PPA) allow you to upload Ubuntu source packages to be built and published as an apt repository by Launchpad. 

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by jerome1232 on 2012-05-10
Run this command and post the output

```
sudo apt-get update
```

Please, wrap the output in code tags by going into advanced mode, highlighting the output and pressing the # symbol.

---

### Post by philinux on 2012-05-10
Old thread closed

---

