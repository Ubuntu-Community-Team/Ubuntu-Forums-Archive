---
title: "stuck in login screen"
date: 2010-11-21
forum: General Help
---

### Post by neonic on 2010-11-21
Hello,

I'm using ubuntu 10.04 and I recently tried installing certain python libraries. The installation of pyXML failed because python.h wasn't present. I thought I could solve this problem by reinstalling python. So I did:

```

sudo apt-get remove python

```Unexpectedly, this command caused all kinds of other things to be uninstalled (like gnome)
So I closed the terminal and shut down.

When I rebooted, I couldn't get past the login screen anymore. When I enter my password and press enter, I just end up in the login screen again. There's no authentication failure.

Does anyone have a solution to this problem? I prefer not to re-install ubuntu entirely and I'd like to keep my settings and updates.

Thanks.

---

### Post by Hippytaff on 2010-11-21
try booting into recovery mode. From the menu choose to drop into a terminal with networking and do
```

sudo apt-get install python

``` and reboot with
```

sudo shutdown -r now

```I did this once too :-s  can't quite remember if this fixed it or not, let me know how it goes :-)

---

### Post by neonic on 2010-11-21
> **Hippytaff said:**
> try booting into recovery mode. From the menu choose to drop into a terminal with networking and do
```

sudo apt-get install python

``` and reboot with
```

sudo shutdown -r now

```I did this once too :-s  can't quite remember if this fixed it or not, let me know how it goes :-)

Nope! That didn't work. Python appeared to be still installed. The system also did all kinds of repairs, but I still don't get through the ligin screen.

---

### Post by Hippytaff on 2010-11-21
ok...you could try reinstalling Gnome/ubuntu desktop. If your happy to try this do
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```
by getting to the terminal with networking as above :-)

---

### Post by neonic on 2010-11-21
> **Hippytaff said:**
> ok...you could try reinstalling Gnome/ubuntu desktop. If your happy to try this do
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```by getting to the terminal with networking as above :-)

I consider this my last resort, because then I'd lose my settings.

I have tried already:
```
sudo apt-get install gnome
```.. but gnome appears to be dependent on two packages and if you install one of these two, the other one is removed. So it doesn't work that way.


To get ubuntu working again, I guess I should re-install the right packages in the right order. Does anyone have a list?

---

### Post by Hippytaff on 2010-11-21
this any good?
[http://www.gnome-db.org/Dependencies](http://www.gnome-db.org/Dependencies)

---

### Post by neonic on 2010-12-03
I have solved the problem like this...

on another machine with the same ubuntu, I listed all the installed packages like this:

```
dpkg --get-selections > installed-software.txt
```

back at my own machine, I installed the packages and now I can login again.

Thanks to everyone who's been helping!

---

