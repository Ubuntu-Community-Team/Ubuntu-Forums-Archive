---
title: "Toolbars+Moving files as root in Kubuntu"
date: 2009-12-05
forum: General Help
---

### Post by Ganjafreak on 2009-12-05
I was wondering how do I get a Awm theme manager like the one from Ubuntu..?

I would like that on Kubuntu and I know it's possible I've seen people with screenshots of there desktops that had it.


And another thing how do I move files as a root user in Kubuntu, See I gave my self all permission controls for everything but it still pops up and says Permission denied I was trying to move a new Icon pack to a "icons" folder in the /usr/share directory

I know for Ubuntu it's "$ sudo nautilus" But that didn't work with Kubuntu.

Does ubuntu use "Sudo" and Kubuntu use something else.?

---

### Post by fluffman86 on 2009-12-05
First, don't use "sudo" when running a graphical application.  That can cause problems.  To move files as root in Ubuntu, use ```
gksu nautilus
```
and use ```
kdesu dolphin
``` or ```
kdesu konqueror
``` in Kubuntu.

you can run any of those commands by pressing ALT + F2 or from the Terminal.

And remember to use that *ANY* time you're launching a graphical app.  For example:

gksu gedit
kdesu kate
kdesu kwrite
gksu nautilus
kdesu konqueror
gksu synaptic
gksu gparted

And you can use sudo in any Ubuntu based distro (and others) to run a program as root (temporarily) from the command line:
sudo cp file.cfg /etc/file.cfg
sudo apt-get install programname
sudo apt-get update && sudo apt-get upgrade
sudo photorec
sudo fdisk -l

---

### Post by lemanhkha1 on 2009-12-05
> **Ganjafreak said:**
> I was wondering how do I get a Awm theme manager like the one from Ubuntu..?

I would like that on Kubuntu and I know it's possible I've seen people with screenshots of there desktops that had it.


And another thing how do I move files as a root user in Kubuntu, See I gave my self all permission controls for everything but it still pops up and says Permission denied I was trying to move a new Icon pack to a "icons" folder in the /usr/share directory

I know for Ubuntu it's "$ sudo nautilus" But that didn't work with Kubuntu.

Does ubuntu use "Sudo" and Kubuntu use something else.?
If you want to use nautilus you can install nautilus and type $ sudo nautilus to copy file in root
$ sudo apt-get install nautilus

---

### Post by Zorael on 2009-12-08
Kubuntu renames kdesu to **kdesudo**, for unknown reasons.
```
$ kdesudo dolphin
```
But be careful with root privileges; it's in your long-term best interest to not give yourself permission to everything. :3

---

### Post by Ganjafreak on 2009-12-08
That is very true for hackers, But I dought that a hacker would have a easy term on my pc trying to get into everything. It asks me for permission to even copy or move a file on my Desktop let alone try to do anything wrong.

---

