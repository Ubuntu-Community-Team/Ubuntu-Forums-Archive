---
title: "Uninstalling a forced 32 bit app"
date: 2009-11-29
forum: General Help
---

### Post by blueshiftoverwatch on 2009-11-29
I wanted to run Zsnes but was too lazy to compile it from source. So I used the *dpkg -i --force-architecture Insert_Package_Name.deb* command to brute force it to work. Which has worked on other applications, but apparently not on this one. When I click the Zsnes icon it flashes up on the screen for a second and then goes away.

Other applications that are installed from a package can be managed from Synaptic. But doing a search for Zsnes in Synaptic doesn't come up with anything. How do I uninstall this package?

---

### Post by shanefagan on 2009-11-29
You should be able to remove it via synaptic package manager. Just look in status>installed(local and obsolete)

---

### Post by blueshiftoverwatch on 2009-11-29
> **shanefagan said:**
> You should be able to remove it via synaptic package manager. Just look in status>installed(local and obsolete)
It's not in there.

---

### Post by blueshiftoverwatch on 2009-11-29
I don't think any 32 bit app that's force installed onto a 64 bit architecture shows up there. Because I force installed my 32 bit copy of Nero Linux that way and it's not there as well.

---

### Post by oldos2er on 2009-11-29
> **blueshiftoverwatch said:**
> I wanted to run Zsnes but was too lazy to compile it from source. So I used the *dpkg -i --force-architecture Insert_Package_Name.deb* command to brute force it to work. Which has worked on other applications, but apparently not on this one. When I click the Zsnes icon it flashes up on the screen for a second and then goes away.

Other applications that are installed from a package can be managed from Synaptic. But doing a search for Zsnes in Synaptic doesn't come up with anything. How do I uninstall this package?

** sudo dpkg -r Insert_Package_Name.deb**

---

### Post by blueshiftoverwatch on 2009-11-29
> **oldos2er said:**
> ** sudo dpkg -r Insert_Package_Name.deb**
Thanks, I feel kinda dumb that it was that obvious. For some reason the package name is ZSNES, not zsnes, which I find weird.

Anyone know why the app wouldn't show up in Synaptic?

---

### Post by fluffman86 on 2009-11-29
dpkg != apt

They are similar and use some of the same libraries, but dpkg is a dumb installer, while apt uses a database.

edit: to be more specific, apt-get/synaptic/etc, manage and download files, then use the dpkg command to install them.
[http://ubuntuforums.org/showthread.php?t=72584](http://ubuntuforums.org/showthread.php?t=72584)

---

### Post by blueshiftoverwatch on 2009-11-29
> **fluffman86 said:**
> dpkg != apt

They are similar and use some of the same libraries, but dpkg is a dumb installer, while apt uses a database.

edit: to be more specific, apt-get/synaptic/etc, manage and download files, then use the dpkg command to install them.
[http://ubuntuforums.org/showthread.php?t=72584](http://ubuntuforums.org/showthread.php?t=72584)
Gotcha.

Also, is that a deranged Pikachu in your avatar?

---

