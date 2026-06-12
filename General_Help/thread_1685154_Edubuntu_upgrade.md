---
title: "Edubuntu upgrade"
date: 2011-02-10
forum: General Help
---

### Post by Steam. on 2011-02-10
See here, i don't know whether it is a Server edition or a standard edubuntu, cause that PC has a Q8300 and 3 PCI cards for NComputing virtualization boxes, so i'm guessing its a standard Edubuntu?I need to upgrade it cause its 7.04.

Also, how to upgrade it while offline?

---

### Post by P4man on 2011-02-10
Upgrading from 7.04 ? If its even possible, I wouldnt. Support for it ended years ago. It was only upgradable to 7.10 which is obviously just as EOL, and 7.10 could only be upgraded to 8.04 LTS and only then would you have a long term support version that is still supported and that you could upgrade to 10.04 if you wanted.

This will never work. You will have to do a fresh install. And stick to LTS versions if you dont want a repeat of this in a couple of year. 10.04 is the current LTS. Dont install 10.10 unless you intend to upgrade every year or so.

---

### Post by Steam. on 2011-02-10
M'kay, but this still leaves me on how to find either if it's a Server edition/standard?

---

### Post by P4man on 2011-02-10
No idea, but if it has a GUI, its probably the standard version. Of course  you can install edubuntu and gnome packages on the server version or whatever server packages you need on edubuntu, so it doesnt matter a whole lot. Server version is essentially the same as the others, just without GUI (by default) and with some other packages installed by default. The hardware would be supported by any ubuntu version.

You could also run

```
cat /etc/lsb-release
```

See if it says edubuntu or ubuntu.

---

### Post by P4man on 2011-02-10
(double post)

---

### Post by Steam. on 2011-02-10
If i format the hard drive, will the virtualization still work on the boxes after i install 10.04?

---

### Post by P4man on 2011-02-10
Woha, no idea how ncomputing works. I doubt it will be completely "out of the box" and for sure it will need configuration and I assume the VMs. If you dont know, ask someone who does before you start formatting!

---

### Post by Steam. on 2011-02-10
> **P4man said:**
> Woha, no idea how ncomputing works. I doubt it will be completely "out of the box" and for sure it will need configuration and I assume the VMs. If you dont know, ask someone who does before you start formatting!

I don't know even if it's virtualizing tbh, every user gets a Station unlocked when it's ready, and gets to the login screen.Each user, not just one.

---

### Post by Steam. on 2011-02-10
Okay, got an answer from NComputing about downloading some image:

It's an 8.04 one, but still.How can I jump straight to this without formatting?

In the conditions i need to do this it's impossible to format it cause there's loads and loads of configuration.

---

### Post by P4man on 2011-02-10
I dont think its possible. There is no easy upgrade path from 7.04. If you have /home on a different partition, it might be enough to install 8.04 and mount the old home partition, but frankly, ask someone who knows. Perhaps ncomputing or whoever installed or managed the machine before.

---

### Post by Steam. on 2011-02-15
Ok, me again.Just to make this clear.Can I run an upgrade on the system(from this to that)without those files Ncomputing files being touched?I mean after all, it's just replacing the system files, right?

---

### Post by P4man on 2011-02-15
I have no idea where those files reside, but if they are in /usr or somewhere else than /home, they might well be wiped. 

One way or another, you are not planning  any attempt before you have made a verified backup of the entire system, right? Id also strongly consider making a clone to another machine and experiment with the upgrade process on that machine first.

---

