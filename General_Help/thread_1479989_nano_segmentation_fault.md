---
title: "nano segmentation fault"
date: 2010-05-11
forum: General Help
---

### Post by UnSandpiper on 2010-05-11
Hi,

I have a 10.04 installation upgraded from 9.10 somewhere around the first beta.

However, since a couple weeks I have the problem that I cannot use nano anymore.

```

mypc:~$ nano
Segmentation fault

```

I've tried to do apt-get remove nano then installed but stil the same
Even tried apt-get purge but with no avail.

Any more ideas what I should try?

---

### Post by UnSandpiper on 2010-05-12
Shamelessly bumping my own thread.

---

### Post by chakras on 2011-03-21
I had this issue, turns out I had a LANG entry in my .bashrc file that it didn't like:

1st try unsetting the LANG variable:

#unset LANG
#nano

Just so you know, I now have LANG set to:

LANG=en_US.UTF-8

-niki-

---

