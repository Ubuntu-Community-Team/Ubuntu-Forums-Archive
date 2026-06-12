---
title: "Installing from backed up cache.."
date: 2009-09-03
forum: General Help
---

### Post by varunmagical on 2009-09-03
Hello guys,
I like to do a lot of customization in linux & I format & install it too many times, too frequently.
But When I want to install something, I have to fetch all the packages again from the server.
To avoid doing that, I use AptOnCD to backup my cache & restore it.
Then I use add remove programs or synaptic to install packages.
But I also use many packages from 3rd party repositories.
How can I install those packages?
Also, In the meantime, If packages in repository are upgraded, Old packages are ignored. How to avoid that?

---

### Post by i.r.id10t on 2009-09-03
Why not set up your own local ubuntu mirror?  Took me all of 30 minutes to set up and configure from bare hardware....  You'll need about 30gb of disk space available.

---

### Post by varunmagical on 2009-09-03
> **i.r.id10t said:**
> Why not set up your own local ubuntu mirror?  Took me all of 30 minutes to set up and configure from bare hardware....  You'll need about 30gb of disk space available.

hmm.. I'll google it.
Havnt heard abt it...

---

### Post by drs305 on 2009-09-03
You can use the following command to install debs:
```

sudo dpkg -i /path/*.deb
*then possibly*
sudo apt-get -f install

```

---

### Post by varunmagical on 2009-09-03
> **drs305 said:**
> You can use the following command to install debs:
```

sudo dpkg -i /path/*.deb
*then possibly*
sudo apt-get -f install

```

ya.. I use it often to install no. of debs in a folder.
But My backed up cache contains many versions of same software as cache is collection of base software + updates...
Will it install latest versions automatically?
What want to ask is, If I do that,
Will I have the same software configuration As I had in previous installation ( Except settings, of course!)
I have kubuntu-desktop package installed over ubuntu.
I am afraid of "dpkg hell"

---

### Post by varunmagical on 2009-09-03
I think this solves it... Haven't tried yet!
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

Anyways.. I am marking this as solved!

---

