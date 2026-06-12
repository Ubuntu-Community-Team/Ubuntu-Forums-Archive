---
title: "ubuntu (11?) help please"
date: 2011-05-18
forum: General Help
---

### Post by srs008 on 2011-05-18
okay i'm really new to linux, even newer to ubuntu. i think i am running a version of 11. 
i've been running windows for 12yrs, learning by error. hell knows how many times windows has been re-installed.
i am able to maintain my own machines now... 
i'm messing with linux as home server (meant to be a linux strongpoint)


okay here's the problem
when i first installed linux it ran fine, shared internet via a router. all computers could access net
i tryed installing java. but different versions had problems, eventually i found sun java for ubuntu...
**java is fixed...**
however around when i installed it i started having problems when running it. it seems to write to the video ram, corrupting the screen, intrestingly the mouse cursor is not affected.
(the screen is a jumble of coloured lines)

i also installed squid. (this machine is to Be a household server.)
since i installed squid internet sharing has became buggy, i am having troubles setting it up properly (if you could help me setup webcaching on it, i'd appreciate it)
the internet does not get detected on my windows machines now...
BUT some games can still get out and connect to IP's.
so there is internet access. even if windows is problematic about it

i'm not too fussed about squid running. i'd prefer it, but don't REQUIRE it.

the RIG
it's a IBM thinkcentre (lost model id)
3.00ghz Pentium 4 hyper-threader
1gb of ram
120 or 150GB HD
1GBps Lan port (limited by router, 100mbps connection)
ROUTER is d-link dir-300, 54mbps wifi... 


internet is through DODO (mobile broadband piggybacks on OPTUS)

TO BE CLEAR
** JAVA corrupts screen. any fixes? (this is fixed. update with Canonical partners and synaptic.) **
internet not sharing properly anymore. (squid?)

and can someone also point out how to set up samba properly?

---

### Post by dino99 on 2011-05-18
about java, into synaptic:

remove/purge everything related to java
then install sun-java6-jre

try to solve your problem one by one (java first, then squib)

---

### Post by srs008 on 2011-05-18
well restarting the ubuntu machine now. so just uncheck anything java? (i'm on another machine thankfully).

so you know. i'm a complete linux newbie. i know some of the basics. and that is minimal...

but synaptic = uncheck anything java. accept
reboot. then re-install?

---

### Post by srs008 on 2011-05-18
okay, re-installing sun java.
this person suspects drivers... we are both IBM.
[http://ubuntuforums.org/showthread.php?p=10832145#post10832145](http://ubuntuforums.org/showthread.php?p=10832145#post10832145)

---

### Post by srs008 on 2011-05-18
1 of 4 packages could not be retrieved...
that's new. it downloaded before...
???
[http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.40ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.40ubuntu1_all.deb)
????
let's try manual...
fail. package ain't there. nor is the site

---

### Post by srs008 on 2011-05-18
right. retrying from sunjava...
let's see if those commands work this time

---

### Post by srs008 on 2011-05-18
added the Canonical partners repo... trying install there...

---

### Post by srs008 on 2011-05-18
java was damaged... thanks. now anyone know how to config squid?

or a easy gui app for configuring squid?

---

### Post by srs008 on 2011-05-19
okay. java not fixed. just a lot less likely. needed heavy ram usage and attempt to access machine

(remember it's a home server)
next up is IBM drivers...

---

