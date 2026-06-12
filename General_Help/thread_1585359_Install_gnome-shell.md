---
title: "Install gnome-shell"
date: 2010-09-30
forum: General Help
---

### Post by strumica on 2010-09-30
I wanted to try the gnome3 on freshly installed Ubuntu 10.04, and tried:

*sudo apt-get install gnome-shell*

it didn't worked for me, and I got the following result:

[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages[/I]

I also tried 

*sudo apt-get build-dep gnome-shell*,

but got the same result again.
I tried to find some help on the net, but no luck.
I am talking about FRESHLY installed Ubuntu 10.04, apt-get updated right away. Is something wrong with the image I downloaded from ubuntu.com, my hardware, or else...?

---

### Post by oldos2er on 2010-09-30
Check to see if you have the universe repository enabled (System, Administration, Software Sources).  

If you like to live dangerously, there's always [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by strumica on 2010-09-30
Everything is enabled but "source code"

---

### Post by oldos2er on 2010-09-30
Have you run ```
sudo apt-get update
``` lately?

---

### Post by BigCityCat on 2010-09-30
I always get

The following packages have unmet dependencies:
  libgjs-dev: Depends: libgjs0 (= 0.5-1ubuntu2.2) but it is not going to be installed
              Depends: xulrunner-dev (< 1.9.2.9~) but 1.9.2.11~hg20100928r34619+nobinonly-0ubuntu1~umd1~lucid is to be installed
E: Build-dependencies for gnome-shell could not be satisfied.

---

### Post by jelofson on 2010-10-03
Ditto. Same thing here.

---

### Post by my92agsr on 2010-10-06
Same problem here.  Anyone have a solution? I've tried downloading libgjs other plaes, as well as xulrunner.  No dice.

---

### Post by xircon on 2010-10-06
The problem is xulrunner, try:

```
sudo aptitude install gnome-shell
``` it should give you the option to downgrade.

---

### Post by BigCityCat on 2010-10-06
That worked thanks.

---

### Post by xircon on 2010-10-06
Does it run OK, I can install, but I can't get the bloody thing to run properly!!  Think it is a problem with my ATI card.

---

### Post by teddybairs1 on 2010-10-13
I just tried that solution and then it told me that it wanted to remove 71 packages, I had to kill the terminal to stop it. any other ideas?

---

