---
title: "How do I install db.h?"
date: 2009-08-14
forum: General Help
---

### Post by lightnb on 2009-08-14
I have  db4.7-util installed, but I'm getting the error:

```

checking db.h usability... no
checking db.h presence... no
checking for db.h... no
configure: error: BDB/HDB: BerkeleyDB not available

```

How do I install db.h?

---

### Post by sdennie on 2009-08-14
Try:

```

sudo apt-get install libdb4.7-dev

```

That should give you the headers for Berkley db.

---

### Post by elram on 2010-03-04
I have the same problem, and tried to follow this advice. But why do I get the error message that libdb4.7-dev package is not found?

---

### Post by gmargo on 2010-03-04
What Ubuntu version are you using?

---

### Post by pacsum on 2010-03-04
> **lightnb said:**
> I have  db4.7-util installed, but I'm getting the error:

```

checking db.h usability... no
checking db.h presence... no
checking for db.h... no
configure: error: BDB/HDB: BerkeleyDB not available

```

How do I install db.h?

.

---

### Post by elram on 2010-03-18
I am using the Jaunty Jackalope.

---

### Post by gmargo on 2010-03-18
> **elram said:**
> I am using the Jaunty Jackalope.
For 9.04 Jaunty, the **libdb4.7-dev** is the right package to install, and it's in the main repository. [http://packages.ubuntu.com/jaunty/libdb4.7-dev](http://packages.ubuntu.com/jaunty/libdb4.7-dev)

Perhaps you need to fix your software sources?  Or do an update?

---

### Post by elram on 2010-03-19
How would I fix my software sources? I have no idea.

I already tried to do the updates with these commands:
apt-get update
apt-get install build-essential
it didn't change anything.

---

### Post by gmargo on 2010-03-19
And what do you get for this?
```

apt-get install libdb4.7-dev
```You can edit software sources in the System &#8594; Administration  &#8594; Software Sources menu
[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

---

### Post by elram on 2010-03-21
```
apt-get install libd4.7-dev
```
says (I try to translate in english):
```

Reading package lists... Ready
Forming the tree of dependencies
Reading state data... Ready
E: Package libd4.7-dev not found
```

---

### Post by Okuryo on 2010-05-16
> **elram said:**
> ```
apt-get install libd4.7-dev
```
says (I try to translate in english):
```

Reading package lists... Ready
Forming the tree of dependencies
Reading state data... Ready
E: Package libd4.7-dev not found
```

I don't know if it's still relevant, but it should be
```
libdb4.7-dev
```
and not
```
libd4.7-dev
```

---

### Post by carlos@idfx on 2011-02-10
> **elram said:**
> ```
apt-get install libd4.7-dev
```says (I try to translate in english):
```

Reading package lists... Ready
Forming the tree of dependencies
Reading state data... Ready
E: Package libd4.7-dev not found
```
 Dude!, you have to include sudo in front of the other stuff. That is super important.
```
sudo apt-get install libd4.7-dev
```
just cut and paste and you're off to the races.
I've been trying to get OpenLdap to work for at least 2 weeks now and I feel like I've read the whole internet trying to get to the bottom of the 10,000 ways the install can go wrong. I am getting the BerkeleyDB installed right now and I'm hoping that's the cure to all my ills!
Good Luck and don't give up.

---

