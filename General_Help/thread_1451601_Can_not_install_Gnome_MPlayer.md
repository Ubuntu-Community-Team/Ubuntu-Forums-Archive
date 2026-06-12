---
title: "Can not install Gnome MPlayer?"
date: 2010-04-10
forum: General Help
---

### Post by georgemad on 2010-04-10
After finished a partial update, the system automatically removed my dear Gnome Mplayer, when I try to install again, it says:

[COLOR=Red]eading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome-mplayer: Depends: libasound2 (> 1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
                 Depends: mplayer (>= 1.0~) or
                          mplayer-nogui (>= 1.0~) but it is not going to be installed
E: Broken packages
[/COLOR]

Can anyone help me? Thanks

---

### Post by wojox on 2010-04-10
Do you have Backports enabled?

---

### Post by georgemad on 2010-04-10
No, what should I do to fix this problem?

---

### Post by Ferrat on 2010-04-10
> **georgemad said:**
> No, what should I do to fix this problem?

maybe try and enable them?

---

### Post by wojox on 2010-04-10
Try opening synaptic and going to Custom Filters > Broken and see if you can fix it.

---

### Post by hikaricore on 2010-04-10
I assume you're using Lucid.  These things happen and you should just ignore partial upgrades if they're going to remove something.
Pay attention next time.

---

