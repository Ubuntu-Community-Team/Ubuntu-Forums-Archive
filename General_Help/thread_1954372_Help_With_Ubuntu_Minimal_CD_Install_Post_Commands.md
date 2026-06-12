---
title: "Help With Ubuntu Minimal CD Install Post Commands"
date: 2012-04-08
forum: General Help
---

### Post by carmenin87 on 2012-04-08
I've been playing with the minimal install CD and have found several articles about what commands to run after the install has finished.

The best set of instructions I have found that appear to give the look of Ubuntu with fewer apps seems to be the ones below. 

1.  sudo apt-get update
2.  sudo apt-get install ubuntu-desktop --no-install-recommends
3.  sudo apt-get install indicator-applet-complete indicator-applet
4.  sudo apt-get install firefox
5.  sudo reboot h now

Could someone help me understand what these commands do, especially the commands in line 1, 2 and 3?

Also, am I missing anything, will these commands ensure that I get proper security updates?  During the command line install, I selected no automatic updates because that was the default and I prefer to install them myself when they are available.  I'm assuming I will get the prompts.

Thank you

---

### Post by carmenin87 on 2012-04-08
Anyone?

---

### Post by Cheesemill on 2012-04-08
```
apt-get update
```Updates the package list stored on your computer so that it knows what software is available for installation.

```
apt-get install <program>
```Will download and install <program> onto your computer.

Because the apt-get command needs to access files on your computer that are usually out of bounds it needs to be run with super user privileges. This is done by prefacing the command with sudo (**s**uper **u**ser **do**).


To upgrade all of the software on your computer to the latest version available just type:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jerrrys on 2012-04-09
2.  sudo apt-get install ubuntu-desktop --no-install-recommends

uduntu desktop package is a complete ubuntu install.  By adding no-recommends, all recommended packages will not be installed. A full ubuntu download is 600+MB and no-recommend download is 160MB. Making a somewhat lighter but not faster system.  The link below is a list of all installed packages.  The bottom portion of that list is all recommended packages.

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

---

