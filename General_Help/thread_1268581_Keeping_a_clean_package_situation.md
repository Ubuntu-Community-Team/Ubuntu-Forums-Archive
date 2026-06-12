---
title: "Keeping a clean package situation"
date: 2009-09-17
forum: General Help
---

### Post by keta on 2009-09-17
Hi all,

Sometimes I install some program via Synaptic, and soon thereafter I realize that I don't need it anymore. Right, I go to Synaptic and uninstall the package. But that leaves all packages that where installed as dependencies unchanged, and my computer is full of not-needed packages.

What I want is a way to store a list of installed packages which I know works well, and if later on I want to revert to that situation, just tell Synaptic or dpkg to install or uninstall any needed package and return to the situation of the list. I know there is a way to create the list with dpkg, but what about the next step? Is this feasible?

Thanks in advance,

Keta

---

### Post by wojox on 2009-09-17
You can install deborphan to remove the remaining dependencies:

[http://www.debian-administration.org/articles/134](http://www.debian-administration.org/articles/134)

Then to find all the packages try:

```
sudo dpkg --get-selections > myPackages
```

This will create a file in your user directory with all installed packages.

You may want to run:

```
updatedb
```

First. Hope that helps.

---

### Post by Junosix on 2009-09-17
How about:

sudo apt-get autoremove && sudo apt-get clean

Does that do a similar thing?

---

### Post by wojox on 2009-09-17
apt-get clean removes everything except lock files from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. Thus, if you need to reinstall a package APT should retrieve it again.

apt-get autoclean removes only package files that can no longer be downloaded. 


[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-clean](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-clean)

---

### Post by keta on 2009-09-18
Thanks for the answers guys.

I did a try with deborphan, but
```
deborphan -a
```listed many packages I do not want to deinstall. For instance, it lists stellarium, but I definitely want to keep it. Should I use another command? (The link you post in the first reply isn't working right now.)

As for dpkg, --get-selections is indeed what I wanted to store the list of packages. Isn't there a way to tell dpkg to read the list and let him perform any needed task to return to the state specified in the list? What about --set-selections, how is it used?

---

