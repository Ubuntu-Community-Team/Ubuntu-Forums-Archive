---
title: "Apt-get problems"
date: 2006-01-20
forum: General Help
---

### Post by saxonthebeach908 on 2006-01-20
hey i'm a total ubuntu n00b (been using for about 3 days now), and i've just been installing a few things here and there...i ran into one problem though. Every time i use sudo apt-get to do anything, i get the following error:
> W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

I tried
```
sudo apt-get update
```
to no avail. Thanks for any help.

---

### Post by az on 2006-01-20
Those repositories must be down.  Try removing them from your sources.list.

---

### Post by strazzere on 2006-01-20
I'm no guru, but when I'm using apt-get I need to do it with the sudo command.

Maybe it's just my breezy install?

I do;

sudo apt-get update
sudo apt-get install blah

Edit: I'm assuming that "to no avail" is meaning your getting an error message when you do an update...

---

### Post by strazzere on 2006-01-20
Ops double post ;\

---

### Post by GeneralZod on 2006-01-20
[QUOTE=saxonthebeach908]
```
apt-get update
```
to no avail. Thanks for any help.[/QUOTE]

Just to make sure - did you type that, or 

```
sudo apt-get update
```?

The former won't actually work :)

Edit:

Wow - beaten by seconds! :)

---

### Post by carlosqueso on 2006-01-20
Methinks the freecontrib repos don't exist any longer.  They can be removed from your /etc/apt/sources.list or commented out with the "#".

---

### Post by saxonthebeach908 on 2006-01-21
Thanks guys, I fixed it by commenting out the freecontrib lines in my sources.list
(Sorry I forgot to include the sudo command in my original post, though I was using it when i ran apt-get update)

Thanks again.

---

