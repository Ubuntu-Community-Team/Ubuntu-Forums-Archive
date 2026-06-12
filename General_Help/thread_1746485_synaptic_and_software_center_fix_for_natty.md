---
title: "synaptic and software center fix for natty"
date: 2011-05-01
forum: General Help
---

### Post by Big_tone on 2011-05-01
I had a problem with synaptic package manager and Ubuntu software center when I upgraded to 11.04, two days ago. They simply would not work for me. There are a few fixes for this on the forums but, I think this one is the simplest and worked for me.

1 - pull up a terminal
2- type the following command: sudo nautilus
     you will be prompted for your password. After entering your password, you will have root access to files and folders.
3 - navigate to file system>var>lib>apt
     inside the "apt" folder you will see a folder called "lists".  Rename it to lists.bak
4 - close the file browser and terminal
5 - reopen terminal and type: sudo apt-get install update

After the update finishes, you will have a new "lists" folder and synaptic package manager/Ubuntu software center should work.

---

### Post by chazdg24 on 2011-05-06
That doesn't work for me.  I get the following error when opening Update Manager and Synaptic:

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Anybody have an idea what to do about this.  I made this mess by trying to install Gnome 3 using installing sudo apt-get install aptitude from the tutorial below.  Big mistake.  Help please, I'm at a loss.

[https://sites.google.com/site/000menu/home/gnome---3]("https://sites.google.com/site/000menu/home/gnome---3")

Further in step 1 I get the following message:


Initializing nautilus-gdu extension

** (nautilus:3440): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '3440'

(nautilus:3440): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by bmbaker on 2011-05-06
> **chazdg24 said:**
> That doesn't work for me.  I get the following error when opening Update Manager and Synaptic:

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Anybody have an idea what to do about this.  I made this mess by trying to install Gnome 3 using installing sudo apt-get install aptitude from the tutorial below.  Big mistake.  Help please, I'm at a loss.

[https://sites.google.com/site/000menu/home/gnome---3](https://sites.google.com/site/000menu/home/gnome---3)

open up a terminal and type
```
sudo gedit /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
```look through to where it says "ain" and add a "m" to it so it says "main"
hit save and close gedit
then in the terminal type
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
```
then your good to go :-)

---

### Post by chazdg24 on 2011-05-06
Didn't work, I get the following when changing "ain" to main


E: Type 'main' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
E: The list of sources could not be read.


Please advise when time permits.  Thank you.

By the way, I have given up on Gnome 3 and would just as soon stick with Gnome 2...

---

### Post by chazdg24 on 2011-05-06
Can anybody help, the problem isn't solved!

---

### Post by plucky on 2011-05-06
> **chazdg24 said:**
> Can anybody help, the problem isn't solved!

We need to see the contents of the file so we can tell you what is incorrect.

Post the output from a terminal for ```
cat /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
```

---

### Post by chazdg24 on 2011-05-06
There you go.  Much thanks!

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main
main

---

### Post by plucky on 2011-05-06
> **chazdg24 said:**
> There you go.  Much thanks!

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main
main

Edit the file with ```
gksudo gedit /etc/apt/sources.list.d/gnome3-team-gnome3-natty.list
``` and remove the last "main"

It should look like ```
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu natty main
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu natty main
```

Good Luck

---

### Post by chazdg24 on 2011-05-06
BINGO!!!  Thanks for the quick reply.  

I am asked to do a partial upgrade, which I agreed to.  I hope that that was not a mistake...

---

### Post by chazdg24 on 2011-05-07
Help!  The update was a big mistake.  I actually installed Gnome 3 with distorted graphics.  I remembered that Gnome 3 has issues with  the ATI CCC and drivers.  So I unistalled both and rebooted to a black screen.  I then rebooted into the Recovery Console and was able to install the Generic video driver.  I rebooted again and had a decent looking Gnome 3.  I rebooted one more time and then...

a black screen.  Ubuntu is frozen, so I rebooted and ran various diagnostic tests in Recovery Console to no avail.  Every time I reboot, I get a blank screen.

Any ideas how I should proceed to fix this?  Much thanks in advance.

---

### Post by chazdg24 on 2011-05-07
Can anybody help...

---

### Post by chazdg24 on 2011-05-07
> **chazdg24 said:**
> Can anybody help...

I guess not...

---

