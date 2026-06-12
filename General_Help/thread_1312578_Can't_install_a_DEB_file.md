---
title: "Can't install a DEB file"
date: 2009-11-03
forum: General Help
---

### Post by OldGrantonian on 2009-11-03
I want to install my first Ubuntu app. It's not in the list shown in Synaptic Package Manager:

[http://ichi2.net/anki/](http://ichi2.net/anki/)

I downloaded the DEB file and double-clicked. I got the message:

Dependency is not satisfiable: Python-qt4

I installed Python-qt4 using Synaptic Package Manager.

I again double-clicked on the Anki DEB file. I get the same message :(

I would be grateful for any assistance :)

---

### Post by cdenley on 2009-11-03
What version of ubuntu are you running. Do you have the universe repository enabled?
System>Administration>Software Sources
What is this doing in the security forum?
[http://packages.ubuntu.com/karmic/anki](http://packages.ubuntu.com/karmic/anki)

---

### Post by OldGrantonian on 2009-11-04
> **cdenley said:**
> What version of ubuntu are you running. 

I have 8.04.2 LTS

>  Do you have the universe repository enabled?If I select "Origin" in the left pane of Package Manager, I see:

gb.archive.ubuntu.com/universe 

(plus main, multiverse, and restricted)

---

### Post by nothingspecial on 2009-11-04
Type

```
sudo dpkg -i nameofapp.deb
```

When you get the message about dependencies type

```
sudo apt-get install -f
```

That should install the dependencies along with the original deb file.

:note: you have to be in the directory containg the deb or specify the path to it.:

---

### Post by P4man on 2009-11-04
The webpage says you need Qt4.4. I think the one that comes with ubuntu 8.04 is older than that. The devs of that app suggest adding a repository to fix that, im not entirely sure thats the best way to do it, but if you trust them you could give it a try. Go to system > adminstration > software sources. Go to third party and add

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

let it reload the list, then try again.

---

### Post by cdenley on 2009-11-04
The last thing you want to do is install third party software. The package you want isn't available for hardy, but is for every release since if you want to upgrade. Otherwise, the best alternative would be to add a thirdy party repo meant for hardy which provides the package you need. If there is no repo, then you can look for a .deb file, but dependencies are often an issue when not targeted for a specific release, as you discovered.

---

### Post by OldGrantonian on 2009-11-05
Thanks to cdenley, nothingspecial, and P4man for the userful responses :)

Based on the comments, I've decided to take the plunge and update to version 9.10 Karmic.

My main purpose in loading 8.04.2 LTS Hardy was to ensure that my first Ubuntu was a rock-solid version, because I had to repartition my disk to dual boot with Windows, and do other scary things. Maybe  I should say that these things would be scary in Windows :)

Now that I've spent a few days playing around with Hardy, I might as well go right up-to-date.

BTW: I installed Anki with no problems.

---

