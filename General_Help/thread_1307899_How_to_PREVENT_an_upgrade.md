---
title: "How to PREVENT an upgrade??"
date: 2009-10-31
forum: General Help
---

### Post by emarkay on 2009-10-31
I have an old version of Avidemux, and i get the note to upgrade ssung the GUI updater, but with apt-get upgrade I don't have a choice to individualize.  How can I mark something as: "I know it's old, I want it that way, leave me alone."   :)

---

### Post by emigrant on 2009-10-31
in system>administration>software sorces

select the updates tab and under automatic updates,
untick 'check for updates'

hope that would work.

---

### Post by emarkay on 2009-10-31
Wouldn't that prevent "All upgrades?" 

Oh, BTW, I filed a bug on that - Using Ubuntu terminology, "update" refreshes the repositories, "upgrade" updates Ubuntu.  I know it's silly, but...

---

### Post by todak on 2009-10-31
Using synaptic, search for the package in question, click on the **Package** menu and then tick the box beside **Lock Version**.

---

### Post by slakkie on 2009-10-31
You want to look into pinning.

Let's say, I don't want to upgrade Firefox.

```

dpkg -l firefox
ii  firefox    3.5.4+nobinonly-0ubuntu0.9.10.1 <desc>

```

Then open /etc/apt/preferences (as root). The file may or may not exist.

Add:
```

Package: firefox
Pin: version  3.5.4+nobinonly-0ubuntu0.9.10.1
Pin-Priority: 1001

```

Now you will not upgrade the firefox version with safe-upgrade commands.

---

### Post by emarkay on 2009-10-31
> **todak said:**
> Using synaptic, search for the package in question, click on the **Package** menu and then tick the box beside **Lock Version**.

Excellent! Thanks.  This also prevents apt-get upgrade from seeing it, too?

---

### Post by todak on 2009-10-31
> **emarkay said:**
> Excellent! Thanks.  This also prevents apt-get upgrade from seeing it, too?

Not sure. However look [here]("https://help.ubuntu.com/community/PinningHowto") if it does not.

---

### Post by NCLI on 2009-10-31
> **emarkay said:**
> Excellent! Thanks.  This also prevents apt-get upgrade from seeing it, too?
It doesn't prevent it from seeing it, now, but it does make it avoid updating it, which is what are think you meant to say ;)

---

### Post by todak on 2009-10-31
See specifically [this section]("https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg") to lock a package from the CLI.

---

