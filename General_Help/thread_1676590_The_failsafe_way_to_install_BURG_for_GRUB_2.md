---
title: "The failsafe way to install BURG for GRUB 2"
date: 2011-01-27
forum: General Help
---

### Post by thewho1050 on 2011-01-27
First off, its a lot of trouble finding the right tutorial. The best one i found is ***_[HERE]("http://code.google.com/p/burg/wiki/InstallUbuntu")_***

If you have already attempted, Remove your previous attempt using
```
sudo apt-get autoremove burg
```

Procees to add the following two lines into the sources.list.save file in /etc/apt.  In order to do this, Open a terminal.  

```
su root
(enter your password)

```

Next we will use PICO to edit the file as root

```
pico sources.list.save
```

Add the following two lines at the bottom of the file

```
deb http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main
deb-src http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main 
```

Make sure to change the word ***_lucid_*** to your current OS name (eg. Maverick or jaunty or something)

Press control^O to save the file, and hit enter when the file name comes up at the bottom.

now, exit root privlige.  Type the following commandsone at a time.

```
sudo apt-get install burg
sudo burg-install /dev/sda
sudo update-burg 
```

At this point we should be done!  Use "t" to change the apperance of BURG when you restart.

---

