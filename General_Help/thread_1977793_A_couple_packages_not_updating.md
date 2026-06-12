---
title: "A couple packages not updating"
date: 2012-05-10
forum: General Help
---

### Post by Ertai87 on 2012-05-10
I have a couple packages I'm wondering about.  Every day I run apt-get update/upgrade, and I have a couple packages which keep getting held back.  I'm wondering if I should force-upgrade them or if I should leave it, and why (and also how; I don't know how to force-upgrade a package XD).  Here's the output from apt-get upgrade:

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ibus-hangul nabi
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Thoughts?

---

### Post by philinux on 2012-05-10
Which ubuntu version.

sudo apt-get dist-upgrade

See what it says

---

### Post by Ertai87 on 2012-05-10
12.04

---

### Post by grahammechanical on 2012-05-10
I am guessing that they are held back for a reason. It might be that they do not yet exist but they will do in a day or two. The link is there but the package is not yet ready.

I had this all the time while 12.04 was under development. I also had crashes due to obsolete packages which were supposed to be replaced but weren't for another day or two. So, I am basing my guess on this experience.

Is it causing anything to crash? If not do not worry. Are you still able to use that keyboard layout?

Regards.

---

### Post by Ertai87 on 2012-05-10
No, nothing seems to be wrong.  Just makes me antsy when I see that there's an update that won't install for some reason, so I was wondering why it won't upgrade.

---

### Post by mc4man on 2012-05-10
You might want to install synaptic & ck. out those 2 packages there, at the very least could be more informative

(the last updates to those 2 in ubuntu repos was Nov. 2011 so there's no 'new' packages to be had. Did you upgrade from 10.04? Do you actually use them?

---

### Post by Ertai87 on 2012-05-11
> **mc4man said:**
> You might want to install synaptic & ck. out those 2 packages there, at the very least could be more informative

I took a look under "Update Manager", but it didn't give me anything particularly informative.  Where should I look?

> (the last updates to those 2 in ubuntu repos was Nov. 2011 so there's no 'new' packages to be had. Did you upgrade from 10.04? Do you actually use them?

Yes, I upgraded from 10.04 to 11.10 (or whatever number it was) and now to 12.04.  I don't know exactly what programs those packages refer to, but I'm presuming it has something to do with IBUS Korean input.  I don't use Korean in particular very often, but I use IBUS regularly; in fact I've already used it 3 or 4 times today alone.

---

### Post by mc4man on 2012-05-11
go 
```
sudo apt-get install synaptic
```
Then search synaptic in the Dash & open it. (once open maybe click on the "Reload" icon, then see what it has to say about those 2 packages

Either search them or in lower left box click on "Status", then in upper left box click on "Installed(upgradable)", should then be in the list on right
(screen shows above

---

### Post by Ertai87 on 2012-05-11
> **mc4man said:**
> go 
```
sudo apt-get install synaptic
```
Then search synaptic in the Dash & open it. (once open maybe click on the "Reload" icon, then see what it has to say about those 2 packages

Either search them or in lower left box click on "Status", then in upper left box click on "Installed(upgradable)", should then be in the list on right
(screen shows above

Alright, that did it.  Turns out for the new version they changed some library dependencies, and apt-get wasn't detecting the dependencies so it was just spewing "unable to upgrade" messages.  Synaptic fixed it though.

---

