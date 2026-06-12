---
title: "How to list installed programs?"
date: 2011-09-19
forum: General Help
---

### Post by Aliagha on 2011-09-19
Hi everybody,

I recently installed some programs from their source files, how can check them?
I tried 'dpkg' command but it shows only installed packages
.

---

### Post by oldos2er on 2011-09-19
If you install from source, programs usually go to /usr/local/bin

---

### Post by Frogs Hair on 2011-09-19
I don't if this is the command that you used . It appears to display my installed programs including PPAs  .```
dpkg --get-selections
```

---

### Post by oldfred on 2011-09-19
Welcome to the forums.

In addition to previous posts, i have saved these ways to list installed programs.

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

Reinstall with aptitude (you may have to install aptitude)
Alternative way with aptitude:
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install

Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'

---

### Post by Aliagha on 2011-09-19
Thank you all for your fast replies,

I installed 'jasper' and I can see that in /usr/local/bin but it's not available in the dpkg's list with different options.

---

### Post by TeoBigusGeekus on 2011-09-19
Try with
```
whereis jasper
```
It will list the source files, executables and command pages.

---

### Post by t0p on 2011-09-19
There's also the command **locate** that will locate files whose titles contain a keyword.  So the command

```
locate jasper
``` should show you where jasper files are (though I think you have to do an update first to ensure the files' locations are in the updatedb).

I ave to say, though, that I'm surprised **dpkg --get-selections**doesn't work.  Maybe you have to run an update first?

---

### Post by oldos2er on 2011-09-19
> **Aliagha said:**
> Thank you all for your fast replies,

I installed 'jasper' and I can see that in /usr/local/bin but it's not available in the dpkg's list with different options.

dpkg and any of the package manager front-ends won't "know" about software you've installed from source, which is normal. If you want to keep track of such software, take a look at **checkinstall** [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by wojox on 2011-09-19
> **Frogs Hair said:**
> I don't if this is the command that you used . It appears to display my installed programs including PPAs  .```
dpkg --get-selections
```

What I use as well:

```
sudo dpkg --get-selections > myPackages
```

---

### Post by drs305 on 2011-09-19
And the GUI way, if you have Synaptic installed: File, Save Markings and tick the 'Save Full state'. You can then use the list to import them from Synaptic into your new installation if desired.

---

