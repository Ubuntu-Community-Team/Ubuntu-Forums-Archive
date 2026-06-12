---
title: "cant install nautilus elementary and gloobus preview"
date: 2010-11-14
forum: General Help
---

### Post by anton706 on 2010-11-14
I was following the instructions here:
[http://www.techdrivein.com/2010/08/gloobus-preview-nautilus-elementary.html](http://www.techdrivein.com/2010/08/gloobus-preview-nautilus-elementary.html)
on how to install nautilus elementary and gloobus preview
and they dosn't work here is what the terminal says after I'm trying to install nautilus elementary and gloobus preview
 [http://img517.imageshack.us/content_round.php?page=done&l=img517/241/screenshotxl.png](http://img517.imageshack.us/content_round.php?page=done&l=img517/241/screenshotxl.png)
help me please install them.
edit:its on ubuntu 10.10

---

### Post by anton706 on 2010-11-14
bump

---

### Post by Verbeck on 2010-11-14
even with those errors, you should be able to install nautilus-elementary and gloobus preview

just follow the instructions they gave

in a terminal, run each command separately
```

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get install gloobus-preview
sudo apt-get upgrade
killall nautilus
```

---

### Post by anton706 on 2010-11-14
Not only that it didnt work it also changed  firefox into namoroka
how can i get it back to firefox?

---

### Post by Verbeck on 2010-11-14
namoroka would only get installed if you had the 'ubuntu-mozilla-daily ppa' in the software sources. to remove it 

> **lovinglinux said:**
> As already posted, disable *ubuntu-mozilla-daily*  ppa from Software Sources, remove *firefox* package and install it  again. Doing a re-install of *firefox* package should also  work.

to open software sources, open synaptic, then from the settings menu >repositories , go to the software sources/other software tab.

---

### Post by anton706 on 2010-11-14
and then if i would lunch the commands you given to me gloobus preview and nautilus elementary will be installed?

---

### Post by Verbeck on 2010-11-14
that is the normal way those applications are installed. 

but instead of upgrading the system to install nautilus elementary (sudo apt-get upgrade), you can select the 3 necessary updates from system>administration>update manager. the'll be under the sub heading 'other : ppa:am-monkeyd' or something similar

---

### Post by gandaran on 2010-11-14
> **anton706 said:**
> and then if i would lunch the commands you given to me gloobus preview and nautilus elementary will be installed?
run those commands then nautilus elementary will be installed when you apply the updates or go to the package manager and install it.

---

### Post by silvagroup on 2010-11-15
I was able to install easily enough by following these instructions [http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html]("http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html") but after several days of lost Nautilus function (except for constant crashes) I removed the ppa, also on the same link.
Looks like it would be a very cool addition to Nautilus but it needs major work before it is functional.

---

### Post by Frogs Hair on 2010-11-15
> **silvagroup said:**
> I was able to install easily enough by following these instructions [http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html]("http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html") but after several days of lost Nautilus function (except for constant crashes) I removed the ppa, also on the same link.
Looks like it would be a very cool addition to Nautilus but it needs major work before it is functional.

The link is for Lucid only , your info shows you have 9.04 ?

---

### Post by Frogs Hair on 2010-11-15
Here is a link for the 10.10 PPA.[http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html](http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html)

---

