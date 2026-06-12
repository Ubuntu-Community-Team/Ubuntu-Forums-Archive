---
title: "trying to repair ubuntu desktop, getting broken packages"
date: 2010-09-20
forum: General Help
---

### Post by ryan461 on 2010-09-20
I broke my ubuntu, and im hoping to repair it w/o reinstall. When it boots it gives me an issue and i can run in low graphics mode(which never loads), reconfig graphics, trouble shoot, or restart x. I've been switching over to a cmd terminal trying to fix with:

```

sudo apt-get install ubuntu-desktop

```
This gives says several dependencies are broken and will not be installed.
"sudo apt-get -f install" doesnt help. I've tried sudo tasksel as well with no luck.

---

### Post by CharlesA on 2010-09-20
What does *sudo apt-get -f install* return (error wise)

---

### Post by ryan461 on 2010-09-20
Well just now it had some libraries that could be removed so I ran apt-get autoremove. I ran the command again. It reads the package list and dependency tree. Then it just says 0 upgraded, 0 newly installed and 0 to be removed and not upgraded.

---

### Post by CharlesA on 2010-09-20
If you reboot and you don't get a GUI, try this:

```
sudo apt-get purge ubuntu-desktop
```

Then install it again:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by SlugSlug on 2010-09-20
or try aptitude

```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by ryan461 on 2010-09-20
> **CharlesA said:**
> If you reboot and you don't get a GUI, try this:

```
sudo apt-get purge ubuntu-desktop
```

Then install it again:

```
sudo apt-get install ubuntu-desktop
```

I ran the purge, it says Package ubuntu-desktop is not installed, so not removed.

Installing it says:
```

pack has unmet dependencies:
ubuntu-desktop: depends: checkbox-gtk but it is not going to be installed
gdebi ' '
gdm
gedit
gnome-about
and some others, as well as recommended packages.

```

sudo aptitude reinstall didnt do much, but tried sudo aptitude install seems to be installing it. ill let you know how this goes.

---

### Post by ryan461 on 2010-09-20
> **ryan461 said:**
> I ran the purge, it says Package ubuntu-desktop is not installed, so not removed.

Installing it says:
```

pack has unmet dependencies:
ubuntu-desktop: depends: checkbox-gtk but it is not going to be installed
gdebi ' '
gdm
gedit
gnome-about
and some others, as well as recommended packages.

```

sudo aptitude reinstall didnt do much, but tried sudo aptitude install seems to be installing it. ill let you know how this goes.

K there appears to be conflicts and such. Theres are counters running for open closed, and conflicts. It said no solution found within allotted time, try harder? I said yes but not feeling hopeful.

I probably should say how i broke it, despite how embarassing. I removed python to reinstall it. I was having issues installing some software. I hadnt realized how many programs were written in python for linux, so after installing it everythings not quite the same as it once was.


**EDIT**

i ran sudo aptitude install -f ubuntu-desktop. Some depenencies it wouldnt install, but i was able to run start x and the desktop seems all well. But then i rebooted, and desktop still wont load

---

### Post by ryan461 on 2010-09-20
Its working now, a coworker had me set the sources.list file to use karmic, but i need lucid as im 10.04. So that prevented some system files from being installed properly i guess.

---

### Post by CharlesA on 2010-09-20
Did you upgrade from karmic to lucid originally?

You shouldn't mess around with the sources file normally and installing packages from different releases can have unwanted side effects.

Did you put the original sources.list back?

---

