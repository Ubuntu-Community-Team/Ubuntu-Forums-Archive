---
title: "Broken Package"
date: 2011-03-09
forum: General Help
---

### Post by MagnaFX on 2011-03-09
Trying to install Usplash, getting this error message

```

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
procps : Depends: upstart-job
Depends: initscripts but it is not going to be installed

usplash : Depends: upstart-job
Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
Depends: upstart (>= 0.6.3-4) but it is not going to be installed
Recommends: usplash-theme-ubuntu but it is not going to be installed

or

Usplash-theme

E: Broken packages


```

---

### Post by nomko on 2011-03-09
You need to install the missing packages:
initramfs-tools 
initscripts
upstart
usplash-theme-ubuntu 
upstart-job

---

### Post by MagnaFX on 2011-03-09
There is where i am having the problem, when i try and install them i is saying that the latest version is already installed.

---

### Post by nomko on 2011-03-09
> **MagnaFX said:**
> There is where i am having the problem, when i try and install them i is saying that the latest version is already installed.
 
If you get that message, just ignore it and click on the install button. It won't do any harm, it will only overwrite the existing files and/or update them. I do have sometimes the same message when i install packages. Try that.

---

### Post by MagnaFX on 2011-03-09
That is not working, i am using 
```
 sudo apt-get update
sudo apt-get install upstart-job

```
And then it shoots back

```
upstart is already the newest version
```

---

### Post by nomko on 2011-03-09
> **MagnaFX said:**
> That is not working, i am using 
```
 sudo apt-get update
sudo apt-get install upstart-job

```
And then it shoots back
 
```
upstart is already the newest version
```
 
Ok. then you have the very latest version installed. Don't see the point of that package being wrong or not up-to-date. And what about the other packages?

---

### Post by MagnaFX on 2011-03-09
THe other packages are the same, all up to date.

---

### Post by nomko on 2011-03-10
If you go to synaptic, at the left bottom you can make a choice between some options (i.e. status, source, etc.). You have to select status and in the list left top you must look for a line called broken packages or broken dependencies (don't know exactly wat it is since i'm using the Dutch version). Click that line and the broken packages will be shown in the main screen.
 
Which package you see?

---

