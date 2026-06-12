---
title: "login problem"
date: 2011-01-02
forum: General Help
---

### Post by arunthakurmanali on 2011-01-02
hi guys,i am in great need of help.i have no idea what happened to my  OS(ubuntu10.04).it doesn't give me any option to enter my login name  & passwd.i just get a blank(default) login screen.last time when it  worked,i was trying to install GTK+2.8,but due to my mistake i deleted  glib using cmd (sudo apt-get purge glib)and after that i even tried to  launch terminal but it failed to launch.also tried to play media files  using vlc but it didn't work.so i tried to restart my os and finally got  stuck in the problem.i have no idea what to do,please help.Is there any  cmd to see what problem occurred or which package is missing

---

### Post by SnickerSnack on 2011-01-02
So...you can log in, right?  When you do, are you sitting at a command prompt?  If so, try

apt-get install glib

maybe that will fix things.  Did you remove anything else?

If you're sitting in a window environment without being able to open a terminal, press CTRL-ALT-F1.  I forget the name for this, but you basically get a terminal.

---

### Post by arunthakurmanali on 2011-01-02
> **SnickerSnack said:**
> So...you can log in, right?  When you do, are you sitting at a command prompt?  If so, try

apt-get install glib

maybe that will fix things.  Did you remove anything else?

If you're sitting in a window environment without being able to open a terminal, press CTRL-ALT-F1.  I forget the name for this, but you basically get a terminal.
I did what you asked me to but it says package is already installed.Is there something else i can do because i really don,t want to format.

---

### Post by dino99 on 2011-01-02
the last choice before reinstallation:

make a cold boot and select: recovery mode, then repair packages, then continue normal boot.

---

### Post by arunthakurmanali on 2011-01-02
> **dino99 said:**
> the last choice before reinstallation:

make a cold boot and select: recovery mode, then repair packages, then continue normal boot.
I did the same, entered recovery mode but problem is that my repair option doesn't show me anything.Is there any command to do so.

---

### Post by dino99 on 2011-01-02
sadly its the hard way to learn :(

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by arunthakurmanali on 2011-01-02
> **dino99 said:**
> sadly its the hard way to learn :(

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Is there any way to talk to the moderators of this forum.maybe they can help me.

---

### Post by MadnessRed on 2011-01-02
try:
sudo apt-get install ubuntu-desktop

Might get all the packages you need back.

---

### Post by Vigh on 2011-01-02
from recovery menu- drop to terminal/command console with networking, make sure you are connected to the network with ether-net, preferably with a wired ether-net connection and Internet connected then (sudo apt-get install ubuntu-desktop), (sudo apt-get update) then (sudo apt-get upgrade) may also fix your problem

without brackets obviously when you enter the commands

---

### Post by arunthakurmanali on 2011-01-02
> **Vigh said:**
> from recovery menu- drop to terminal/command console with networking, make sure you are connected to the network with ether-net, preferably with a wired ether-net connection and Internet connected then (sudo apt-get install ubuntu-desktop), (sudo apt-get update) then (sudo apt-get upgrade) may also fix your problem

without brackets obviously when you enter the commands

Is there any relation of my problem to Xserver.....(something like this)?

---

### Post by arunthakurmanali on 2011-01-02
> **MadnessRed said:**
> try:
sudo apt-get install ubuntu-desktop

Might get all the packages you need back.
Is there any relation of my problem to Xserver.....(something like this)?

---

### Post by MadnessRed on 2011-01-02
> **arunthakurmanali said:**
> I did what you asked me to but it says package is already installed.Is there something else i can do because i really don,t want to format.

Do what you did here, exactly the same but install the package ubuntu-desktop.
sudo apt-get install ubuntu-desktop

The problem is that when you removed glib, anything that requires glib will also have been removed. Installing ubuntu-desktop should put back everything that ubuntu needs, hopefully.

---

### Post by Vigh on 2011-01-02
remove and purge ubuntu-desktop and reinstall

make sure you do reinstall though or you won't get a screen to control, just a command terminal

sudo apt-get remove --purge ubuntu-desktop

then importantly

sudo apt-get install ubuntu-desktop

---

### Post by MadnessRed on 2011-01-02
> **arunthakurmanali said:**
> Is there any relation of my problem to Xserver.....(something like this)?
Possibly but it is more likely something to do with gnome. When you removed glib, anything that required glib was also removed. I did the same thing quite a while ago.

---

### Post by arunthakurmanali on 2011-01-03
> **MadnessRed said:**
> Do what you did here, exactly the same but install the package ubuntu-desktop.
sudo apt-get install ubuntu-desktop

The problem is that when you removed glib, anything that requires glib will also have been removed. Installing ubuntu-desktop should put back everything that ubuntu needs, hopefully.
I did what you asked me to(installed desktop) but again no luck.Do you have anyother option,anyway thanks for help.

---

### Post by arunthakurmanali on 2011-01-03
> **Vigh said:**
> remove and purge ubuntu-desktop and reinstall

make sure you do reinstall though or you won't get a screen to control, just a command terminal

sudo apt-get remove --purge ubuntu-desktop

then importantly

sudo apt-get install ubuntu-desktop
I exactly followed your cmds i.e first removed desktop and installed it again,but it didn't work again.thanks for help.

---

### Post by sikander3786 on 2011-01-03
Please confirm you can successfully get to the GDM Login Screen but can't see any options to log in?

From the command line, try these.

```
dhclient eth0
```

This will bring up your internet. Replace eth0 with your network interface.

One-by-one:
```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by arunthakurmanali on 2011-01-04
> **sikander3786 said:**
> Please confirm you can successfully get to the GDM Login Screen but can't see any options to log in?

From the command line, try these.

```
dhclient eth0
```This will bring up your internet. Replace eth0 with your network interface.

One-by-one:
```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update && sudo apt-get upgrade
```
yes its for sure i can't login as there no place to enter my user name & passwd.its just a splash screen or default screen of ubuntu.do you know how to login through cmd line in grub.I also tried the comnds you gave me.output of install -f was -reading dependency......
0 upgraded,0 new installed,0 to remove.configure --a showed nothing.should i reconfigure my xorg file? thanks

---

### Post by sikander3786 on 2011-01-05
You can try reconfiguring XORG but I don't think that would help much. Lets see. Here are the commands.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

---

### Post by arunthakurmanali on 2011-01-05
> **sikander3786 said:**
> You can try reconfiguring XORG but I don't think that would help much. Lets see. Here are the commands.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
``````
sudo dpkg-reconfigure -phigh xserver-xorg
```Reboot.
I tried your cmds 1st one said -no such file,while 2nd commnd had no output( i took risk without creeating bkup file).I feel i am really exhausted of this problem:mad:.Thanks anyway for your support.

---

