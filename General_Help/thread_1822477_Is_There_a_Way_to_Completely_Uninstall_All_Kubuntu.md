---
title: "Is There a Way to Completely Uninstall All Kubuntu Related Things?"
date: 2011-08-10
forum: General Help
---

### Post by moore.bryan on 2011-08-10
I'm a long-time GNOME user who wanted to check-out how far KDE and Kubuntu have come on my Oneiric machine, so I installed kubuntu-desktop and logged-in to my new Kubuntu desktop. After fumbling around for the past few days, I've come to one major realization: I am most definitely *not* a KDE guy.

Now, I'm no Linux noob, but for the life of me I can't figure-out how to uninstall all the random things the kubuntu-desktop meta-package installed. Uninstalling kubuntu-desktop of course doesn't solve the problem because it's just a meta-package. I'm sure it's as simple as a CLI input, but I can't seem to get to that part of my memory. Both apt-get remove --purge and aptitude purge *do not* get rid of all the random programs.

Help!?

---

### Post by Ad1217 on 2011-08-10
I did this a while back... however, removing ALL kubuntu related things messed my computer up alot... I ended up having to reinstall. make sure you are not using any kde applications before you do this ( if you are, write them down somewhere (or rethink this)).
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

edit: oh, by the way, --purge only removes configuration files

---

### Post by moore.bryan on 2011-08-10
Unfortunately, the files listed are for 11.04 and not my Oneiric install. :-(. I thought there was a CLI command for listing all packages a meta-package installs; any ideas about that?

---

### Post by haresear on 2011-08-10
> **moore.bryan said:**
> Unfortunately, the files listed are for 11.04 and not my Oneiric install. :-(. I thought there was a CLI command for listing all packages a meta-package installs; any ideas about that?

This may not be that convenient, but "apt-get -s install kubuntu-desktop" should give you a list of everything in the meta-package. You might have to use --reinstall also, since you already have kubuntu installed.

I think there is a list option with dselect also. I don't have dselect installed, so I can't refresh my memory about that.

---

### Post by lordadi on 2011-08-10
Wouldn't ```
sudo apt-get autoremove
``` do the trick? It ***should*** find all KDE files that are not in use at the moment and mark them for removal.

---

### Post by Ad1217 on 2011-08-10
oh, sorry, didn't see that.

---

### Post by moore.bryan on 2011-08-11
> **haresear said:**
> This may not be that convenient, but "apt-get -s install kubuntu-desktop" should give you a list of everything in the meta-package. You might have to use --reinstall also, since you already have kubuntu installed.

I think there is a list option with dselect also. I don't have dselect installed, so I can't refresh my memory about that.
The -s option simply tells me about the metapackage kubuntu-desktop, it doesn't tell me about the packages installed by it.
:-(

dselect was a *great* idea; I hadn't thought about that! But, it's so unwieldy, I don't wonder why it's not installed by default! And, unfortunately, it doesn't give me any usable way to get rid of my KDE stuff.

> **lordadi said:**
> Wouldn't ```
sudo apt-get autoremove
``` do the trick? It ***should*** find all KDE files that are not in use at the moment and mark them for removal.
The autoremove option would uninstall unnecessary/unused packages, but the kubuntu-desktop metapackage is unnecessary to begin with *because* it's a metapackage; i.e., it can be uninstalled without harming the packages it previously installed.

I made some movement forward by downloading the kubuntu-desktop .deb, unpacking it, and looking at the dependencies. The problem is it lists some packages--like cups and gstreamer--that my GNOME install needs. So, it looks like I'll just have to go package-by-package and uninstall things one-by-one.

If any dev comes along to this thread, which I know is highly unlikely because they don't usually lurk here, *please* give apt a way to completely uninstall a metapackage **and** the packages it installs!

---

### Post by westie457 on 2011-08-11
Hi

I know this has nothing to do with the command line.
Have you tried using 'Computer Janitor' to find and remove unused packages?

It usually works for me.

---

### Post by haresear on 2011-08-11
> **moore.bryan said:**
> The -s option simply tells me about the metapackage kubuntu-desktop, it doesn't tell me about the packages installed by it.
:-(


On my Xubuntu 11.04 box, when I execute "apt-get -s install kubuntu-desktop" I get a list of all the additional packages that it is going to install. I guess because you have kubuntu-desktop already installed, it no longer provides that list. Adding "--reinstall" apparently doesn't provide any additional info. Sorry, I'm out of ideas.

---

### Post by debd on 2011-08-11
apt-get autoremove should usually be sufficient.. to remove packages that were automatically installed to satisfy dependencies for some package and are no more needed.

Otherwise you can run ```
apt-cache depends kubuntu-desktop
```
which will show you a list of packages kubuntu-desktop depends upon.. but there will be listing of no-orphan packages too .. on which GNOME depends as well.

---

### Post by moore.bryan on 2011-08-11
> **debd said:**
> apt-get autoremove should usually be sufficient.. to remove packages that were automatically installed to satisfy dependencies for some package and are no more needed.

Otherwise you can run ```
apt-cache depends kubuntu-desktop
```
which will show you a list of packages kubuntu-desktop depends upon.. but there will be listing of no-orphan packages too .. on which GNOME depends as well.
This is *exactly* the problem I was trying to get away from, but "solved" my issues by biting the bullet and using Synaptic. I searched for "kde" in package names and descriptions and then deleted each one one-by-one. By doing it that way, I could see if removing the package also required other packages to be deleted. Finally back to normal, without KDE stuff; however, the original "problem" still exists. That is, there should be an *easy* way to delete a metapackage and have an interactive message about removing the dependencies, as well.

---

### Post by MARP1961 on 2011-08-11
I blitzed Kubuntu desktop from my Ubuntu installation by opening Synaptic Package Manager and deselected any mention of Kubuntu or KDE. This took a while but did the trick.

Virtualbox or a live CD is a good way of trying different things out before installing them.

---

### Post by moore.bryan on 2011-08-11
The blitz is what I eventually did... I've tried virtuals in the past, but they don't work particularly well on my netbook.

---

### Post by sisco311 on 2011-08-11
You can list the dependencies of a package with:
```
apt-cache depends **package**
```

ubuntu-desktop and kubuntu-desktop have some common dependencies, so you don't need to uninstall all dependencies of kubuntu-desktop.

You can try something like this:

Save the dependencies of ubuntu-desktop in a file:
```
apt-cache depends ubuntu-desktop | awk '/Depends|Recommends/{print $2}' > ubuntu-desktop
```

Save the dependencies of kubuntu-desktop in another file:
```
apt-cache depends kubuntu-desktop | awk '/Depends|Recommends/{print $2}' > kubuntu-desktop
```

Delete the common dependencies from kubuntu-desktop:
```
while read -r package; do sed -i "/$package/d" kubuntu-desktop; done < ubuntu-desktop
```

Now the kubuntu-desktop file should contain the packages you want to remove, but you may have to manually delete some packages from the list. You can try to remove the packages listed in the file with:
```
sudo apt-get remove $(< kubuntu-desktop)
```

Now you have to make sure that all the packages from ubuntu-desktop are installed:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by moore.bryan on 2011-08-11
This is a good suggestion, but not an elegant solution. I would have thought much of this would be automated by apt by now... I guess I was hoping for too much. Perhaps it's time to learn some code and write a script/program... ;-)

---

