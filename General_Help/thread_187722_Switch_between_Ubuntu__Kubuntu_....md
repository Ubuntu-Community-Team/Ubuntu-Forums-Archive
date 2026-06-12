---
title: "Switch between Ubuntu / Kubuntu ..."
date: 2006-06-03
forum: General Help
---

### Post by johann_p on 2006-06-03
I really do not understand why this distinction between Ubuntu and Kubuntu by making them different distros is made. I installed "Kubuntu" by apt-get from a running Ubuntu.
Why this seemingly artificial and unnecessary big gap just because of the desktop that is used?

Now I get the "Kubuntu" logo each time when booting. 

Is it possible to show the Ubuntu logo and still have all of KDE (desktop manager and apps) installed in parallel with GNOME, e.g. as in Suse?

How can I dynamically change the display manger between kdm and gdm?

---

### Post by Rackerz on 2006-06-03
I don't know about the kubuntu logo, what command did you use to install the KDE desktop enviroment?

To change between kdm and gdm you will need to logout and choose session options and change to kde or gdm.

---

### Post by johann_p on 2006-06-03
[quote=Rackerz]I don't know about the kubuntu logo, what command did you use to install the KDE desktop enviroment?

To change between kdm and gdm you will need to logout and choose session options and change to kde or gdm.[/quote]

I think I simply copied I command that I found on the Kubunut website, something like "apt-get install kubuntu" 
Problem is, now that I look again at the website, I am unable to find those instrcutions again ... :(

When I log out I can switch between the different *Window* managers, but not between the two display managers (i.e. I can switch between KDE and GNOME, but not between gdm and kdm, which would be two different ways to show login screens).

---

### Post by tagbre on 2006-06-03
I also use both KDE and Gnome, I solved the boot logo thing by installing the serengeti usplash artwork, which is nicer than the default Ubuntu/Kubuntu artwork. Search for it in the forums. 
As for the KDM/GDM thing, afaik it's not possible to change between them, that's why when u install a second desktop environement, ur prompted to choose either KDM or GDM. I agree that changing sessions requires too many steps...

---

### Post by cjazz on 2006-06-03
To choose display managers, do

```
sudo dpkg-reconfigure gdm
```

and make the choice in the dialogue that follows. You could also do dpkg-reconfigure kdm -- that is, if I correctly understand the question you're asking.

---

