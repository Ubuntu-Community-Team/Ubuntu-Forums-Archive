---
title: "settings not available?"
date: 2010-02-18
forum: General Help
---

### Post by Borbor on 2010-02-18
Hey, I'm trying to get the 190 nvidia drivers to stop my horrible overscan, I've found a great guide to it [here ]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html")but the on the last step I'm getting this result;
```

$ sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings-190
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-190-modaliases is already the newest version.
nvidia-190-modaliases set to manually installed.
Package nvidia-settings-190 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-settings
E: Package nvidia-settings-190 has no installation candidate

```I'm using 9.10, and I know the guide says it's a guide for other releases, but others have just replaced "jaunty" with "karmic" and had it work for them. 
So this may be a noob question, and I'm not really sure where to put it, so move it if it needs to be moved, thanks!

---

### Post by orky7 on 2010-02-18
for a hassel free update use System-> administration -> hardware drivers and install the nvidia drivers.

---

### Post by Borbor on 2010-02-18
for some reason though it's not picking up any new nvidia drivers, only the 185s

---

### Post by wojox on 2010-02-18
You don't need the nvidia-settings-190. Just nvidia-settings

---

### Post by Borbor on 2010-02-18
says nvidia-settings is already the newest version
edit- also, I have version 190 and 195 in my driver list, but it says "systemerror: install archives() failed"

---

### Post by 2hot6ft2 on 2010-02-18
> **orky7 said:**
> for a hassel free update use System-> administration -> hardware drivers and install the nvidia drivers.
That's the recommended way to install restricted graphics drivers in Ubuntu

If you want the latest driver for your card go to the NVIDIA.com website and find the drivers for your card and follow their instructions for installing them. Basically you stop X which is the gui and from the command line as root run the installer.

Here's their instructions for running the installer from their website.
Naturally the package name will be different for yours.

> Starting the Installer

After you have downloaded the file NVIDIA-Linux-x86-190.53-pkg#.run, change to the directory containing the downloaded file, and as the root user run the executable:

# cd yourdirectory
# sh NVIDIA-Linux-x86-190.53-pkg#.run 
It will present you with a few questions that you will select your answer by using the TAB button to move between the options.

That article is 3 months old and version numbers change. Are you positive those are the right ones for your card in the first place?

---

### Post by Borbor on 2010-02-19
I've been trying that, when I use ctrl-alt f1, and init 3, then sh the .run, I get a bunch of "File not found" errors.
I think they should be right for my card, it's a nvidia geforce 9600 gt

---

### Post by sandman3838 on 2010-02-23
I think I have been having the same issue?  

If you find something let me know and I'll do the same.

[http://ubuntuforums.org/showthread.php?t=1414540](http://ubuntuforums.org/showthread.php?t=1414540)

---

