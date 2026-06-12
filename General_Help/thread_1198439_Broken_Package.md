---
title: "Broken Package??"
date: 2009-06-27
forum: General Help
---

### Post by sports fan Matt on 2009-06-27
When I attempt to run update manager..I get E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
This started when pidgin was acting up, but now its ok..Any ideas?

---

### Post by jocko on 2009-06-27
Post the contents of the file /etc/apt/sources.list.d/pidgin-ppa.list, there's probably something wrong there...

---

### Post by sports fan Matt on 2009-06-27
I figured..Whats the command I need..Im having a drawing the blank moment.

---

### Post by drs305 on 2009-06-27
> **sox fan Matt said:**
> I figured..Whats the command I need..Im having a drawing the blank moment.


Since you will have to edit it eventually anyway:
```

gksudo gedit /etc/apt/sources.list.d/pidgin-ppa.list

```

Otherwise "cat /etc/apt/sources.list.d/pidgin-ppa.list" would do...

This is what it should look like if you are using *jaunty*:
> deb [noparse]http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu[/noparse] jaunty main


---

### Post by sports fan Matt on 2009-06-27
Thats exactly what it looks like..If I added the word "jaunty"..Does that fix the problem?

---

### Post by jocko on 2009-06-28
> **sox fan Matt said:**
> Thats exactly what it looks like..If I added the word "jaunty"..Does that fix the problem?
Yes.

---

