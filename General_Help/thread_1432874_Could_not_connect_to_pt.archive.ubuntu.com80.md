---
title: "Could not connect to pt.archive.ubuntu.com:80"
date: 2010-03-18
forum: General Help
---

### Post by edup_pt on 2010-03-18
I,

Since yesterday im having a message that i cant connect to: "Could not connect to pt.archive.ubuntu.com:80 (193.136.212.166). - connect (111: Connection refused)"

It seems that the link is broken. Does anyone nows what is happening?

Thanks.

Eduardo

---

### Post by slakkie on 2010-03-18
for a quick fix:

```

sudo perl -p -i.ORIG -e 's/pt.ar/nl.ar/' /etc/apt/sources.list
sudo aptitude update
sudo aptitude safe-upgrade

```

Your original sources.list can be found at /etc/apt/sources.list.ORIG

Not too long ago a country men of yours had the same problem. Maybe an there is an issue with the mirror. Dunno.

---

### Post by edup_pt on 2010-03-23
Thanks. It worked :)

It's really a mirror problem.

---

### Post by jalms on 2011-08-26
Unluckily, it didn't work for me.
The command 
sudo perl -p -i.ORIG -e 's/pt.ar/nl.ar/' /etc/apt/sources.list worked but the command for aptitude just resulted in "Operation aptitude invalid".

Could you please help?

---

