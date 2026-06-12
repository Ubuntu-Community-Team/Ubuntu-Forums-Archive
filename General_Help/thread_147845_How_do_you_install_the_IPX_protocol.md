---
title: "How do you install the IPX protocol"
date: 2006-03-20
forum: General Help
---

### Post by HokeyFry on 2006-03-20
I need to install the IPX protocol for some older games I want to run in Ubuntu (descent and descent 2 are a few major titles, have gotten these two properly working) for multiplayer action. But the only things I find have a bunch of crap I do not understand and/or something about compiling it into a kernel. IN windows it's relatively easy to enable IPX but in linux (*as is almost everything in it) it is probably much harder to do.


*Don't get me wrong, I am not complaining about the extra work that must be done to get some things to work in linux. Actually, that's the fun part!

---

### Post by mr.p on 2006-03-20
[QUOTE=HokeyFry]I need to install the IPX protocol for some older games I want to run in Ubuntu (descent and descent 2 are a few major titles, have gotten these two properly working) for multiplayer action. But the only things I find have a bunch of crap I do not understand and/or something about compiling it into a kernel. IN windows it's relatively easy to enable IPX but in linux (*as is almost everything in it) it is probably much harder to do.


*Don't get me wrong, I am not complaining about the extra work that must be done to get some things to work in linux. Actually, that's the fun part![/QUOTE]
Dug this from this thread [http://www.ubuntuforums.org/showthread.php?t=131902&highlight=IPX]("http://www.ubuntuforums.org/showthread.php?t=131902&highlight=IPX").

```

apt-get install ipx
sudo modprobe ipx
sudo ipx_interface add -p eth0 <type> <IP>

```

Probably have to `man ipx_interface` don't know what "<type>" is.

---

### Post by lerkaram on 2006-04-28
I just installed ubuntu on my boss's computer... and I need to get IPX (and for that matter, ncpfs) to install... but I get an error when I try the following:

```

apt-get install ipx

```

```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ipx

```

any ideas whats going wrong? It has been months since I've gotten my desktop to work... and I kinda forgot what I did... any thought would be nice.

-Peter

---

### Post by steve8track on 2007-07-02
lerkaram, try this to update apt-get:

```
sudo apt-get update

```

If you get a GPG error while updating apt-get, try this thread:
[http://ubuntuforums.org/showthread.php?t=188295]("http://ubuntuforums.org/showthread.php?t=188295")

As for the other problem:
> Probably have to `man ipx_interface` don't know what "<type>" is.
I found [this link HERE ]("http://pwet.fr/man/linux/administration_systeme/ipx_interface") which helped me know what the <type> is:
```

sudo ipx_interface add -p eth0 802.2

```

It worked for me.  Hope that helps.

---

### Post by has-sanasif on 2007-09-23
this is what i get when i try to install ipx
apt-get install ipx
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
what do i do to get ipx to work, iwant it for ra2

---

### Post by HokeyFry on 2007-09-23
for that to work append
```
sudo
```
to the beginning of the apt-get line

i never did get IPX to work though, i found a patch for the game i needed it for that let me play multiplayer without it

---

