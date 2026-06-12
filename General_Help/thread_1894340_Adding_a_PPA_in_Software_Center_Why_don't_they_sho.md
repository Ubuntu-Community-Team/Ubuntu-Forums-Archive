---
title: "Adding a PPA in Software Center: Why don't they show up?"
date: 2011-12-12
forum: General Help
---

### Post by diggersf on 2011-12-12
I'm documenting the PPA installation process for novice users. According [this tutorial]("http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu/"), previous versions of Ubuntu Software Center would refresh after adding a PPA via Edit > Software Sources. The latest version does not seem to refresh and if I add a new PPA, I must run sudo apt-get update in a terminal before it shows up. I'd like to avoid sending new users to a terminal.

Has anyone else run into this? Is this a bug?

---

### Post by oldtimer7777 on 2011-12-12
> **diggersf said:**
> I'm documenting the PPA installation process for novice users. According [this tutorial]("http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu/"), previous versions of Ubuntu Software Center would refresh after adding a PPA via Edit > Software Sources. The latest version does not seem to refresh and if I add a new PPA, I must run sudo apt-get update in a terminal before it shows up. I'd like to avoid sending new users to a terminal.

Has anyone else run into this? Is this a bug?

Don't add PPAs that way, do it from the command line instead. It is easier, faster, and if you have an error you will know more about the error itself:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

On the above checklist you will find all the PPAs and how to cut and paste them into your command line terminal.  If you need a different PPA, then you search for the command line instructions for each PPA you want to install on a search engline like google. They aren't very hard to locate.  Don't use the software center to install them, as I have found that way to be slow, and unreliable.  Or if you need a GUI to add repositories, try synaptic package manager instead of software center. If something goes wrong during the installation process, you will know more about what is going on that way, and get a more detailed error message too.  If you need help later on, that information would help us to fix things too.

---

### Post by diggersf on 2011-12-12
Thanks for the reply! The terminal approach certainly works for me, but I'm writing for people who aren't confortable with it. I'm interested in fixing the issue with Ubuntu Software Center so that this is easy for others as well.

---

### Post by oldtimer7777 on 2011-12-12
> **diggersf said:**
> Thanks for the reply! The terminal approach certainly works for me, but I'm writing for people who aren't confortable with it. I'm interested in fixing the issue with Ubuntu Software Center so that this is easy for others as well.

Well the software center is in development right now. And it has some bugs lately. It would be better to wait until LTS to required new Ubuntu users to try that method. Use the well-tested synaptic package manager for now, or use the command line instead. It isn't going to get fixed in the General Help section, so don't bother.  If you want to be a Ubuntu developer, you need to find the correct forum section, because you are in the wrong place for that. This is how this works.

---

### Post by diggersf on 2011-12-12
Great. If you think this is a bug, I'll hunt for a bug report or open one if necessary. Thanks for the help!

---

### Post by oldtimer7777 on 2011-12-12
> **diggersf said:**
> Great. If you think this is a bug, I'll hunt for a bug report or open one if necessary. Thanks for the help!

I don't know if it is bug or not, but I've seen enough issues with the software center posted here in the general help section lately that I would probably recommend you to advise your new ubuntu users to install synaptic package manager instead or simply stick the command line until the next LTS. If you want to be a bug tester, stick with the latest software center and suffer with it.

---

