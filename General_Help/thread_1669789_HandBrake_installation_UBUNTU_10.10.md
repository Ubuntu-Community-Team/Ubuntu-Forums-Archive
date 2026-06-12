---
title: "HandBrake installation UBUNTU 10.10"
date: 2011-01-18
forum: General Help
---

### Post by satyapriyananda on 2011-01-18
How to install HandBrake in Ubuntu 10.10? It is said that HandBrake is very good. I hope that it is really so. I wish to try it. I cannot build etc as I am new to UBUNTU but sincerely learning.

---

### Post by howefield on 2011-01-18
Moved to General Help.

Add this PPA to your sources.list by opening a termianl and typing the following command.

```
ppa:stebbins/handbrake-releases
```

then follow that by

```
sudo apt-get update
```

And finally..

```
sudo apt-get install handbrake-gtk

```


[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)
[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

---

### Post by JohnAStebbins on 2011-01-19
> **howefield said:**
> Moved to General Help.

Add this PPA to your sources.list by opening a termianl and typing the following command.

```
ppa:stebbins/handbrake-releases
```

then follow that by

```
sudo apt-get update
```

And finally..

```
sudo apt-get install handbrake-gtk
```


[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)
[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

You left out the actual command for adding the PPA to sources.list.  The complete set of commands should be:
```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk
```

---

### Post by bruckwine on 2011-12-16
Sweet thanks - new to ubuntu encoding but HB was always good to me on windows :)

---

### Post by tears of the river on 2011-12-16
> **bruckwine said:**
> Sweet thanks - new to ubuntu encoding but HB was always good to me on windows :)

if this your problem is solved then please mark the thread as solved

---

### Post by nothingspecial on 2011-12-16
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

