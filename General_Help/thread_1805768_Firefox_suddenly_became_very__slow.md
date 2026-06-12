---
title: "Firefox suddenly became very  slow"
date: 2011-07-16
forum: General Help
---

### Post by srisharan on 2011-07-16
Today I dont know why,but all of a sudden Firefox became very slow.It is taking ages just to load up a normal text.And why I google something the page I get is completely in black(including all the font).I have disabled all extensions and addons,even purged firefox and installed it again.I am running the latest 5.0.I am truly bewildered by this. :confused: Can I do something to fix this

---

### Post by lovinglinux on 2011-07-16
See:

[http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)
[http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)
[http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

### Post by srisharan on 2011-07-16
Hmm,turned out to be profile problem.Corrected it.By the way yesterday a program I was installing(ansys) opened firefox.It opened it as root.And then when I later opened ff today this problem sprang up.Could there be any relation between the two??

---

### Post by lovinglinux on 2011-07-16
> **srisharan said:**
> Hmm,turned out to be profile problem.Corrected it.By the way yesterday a program I was installing(ansys) opened firefox.It opened it as root.And then when I later opened ff today this problem sprang up.Could there be any relation between the two??

Then the problem is with permissions, if you opened Firefox with sudo instead of gksudo.

See the last item on the list at [http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions)

---

### Post by srisharan on 2011-07-17
No it started that one time as root because that I was installing ansys as root.The software started the browser that one time-kind of a survey it wanted me to take and I just clicked yes  with out seeing.It always started with normal permissions since then but had this problem till I changed the profile

---

### Post by lovinglinux on 2011-07-17
> **srisharan said:**
> No it started that one time as root because that I was installing ansys as root.The software started the browser that one time-kind of a survey it wanted me to take and I just clicked yes  with out seeing.It always started with normal permissions since then but had this problem till I changed the profile

You have lost permission of the profile to root. Then Firefox breaks.

---

### Post by srisharan on 2011-07-17
If I lost permission to root the  would it should asked my password to access root when I deleted it right??It didnt ask me any.

---

### Post by lovinglinux on 2011-07-17
> **srisharan said:**
> If I lost permission to root the  would it should asked my password to access root when I deleted it right??It didnt ask me any.

Perhaps it was just a corrupted profile.

---

### Post by HiImTye on 2011-07-17
if you were running a program as root and it spawned a new program then that new program is also running under root

try this and see if it fixes your problem
```
chown -R <your username> /home/<your username>/
```

---

### Post by lovinglinux on 2011-07-17
> **HiImTye said:**
> if you were running a program as root and it spawned a new program then that new program is also running under root

try this and see if it fixes your problem
```
chown -R <your username> /home/<your username>/
```

The problem is fixed already, we are just discussing the possible culprit.

---

