---
title: "gnome-terminal ignoring prefences set by gconf-editor"
date: 2010-10-02
forum: General Help
---

### Post by cprofitt on 2010-10-02
I have changed the default gnome-terminal preference but it is ignoring the default geometry I set using gconf-editor.

It is opening in 80x24 and I have it set at 100x25 under

apps
- gnome-terminal
--profiles
---Default

Any ideas?

---

### Post by cprofitt on 2010-10-02
I opened up a bug report for this [https://answers.launchpad.net/ubuntu/+source/gnome-terminal](https://answers.launchpad.net/ubuntu/+source/gnome-terminal)

The problem also appears in Fedora 13 so it looks to be a Gnome issue and not just an issue in Ubuntu.

---

### Post by drs305 on 2010-10-02
Is is set to open a profile other than Default (such as Profile0)?  

Does the problem also occur if you create a new profile, set it as the launching profile, and alter its settings?

I mess with the gnome-terminal a lot but haven't experienced your problem.

```
gconf-editor /apps/gnome-terminal/global/default_profile
```

---

### Post by cprofitt on 2010-10-02
Same problem with making a new profile.

What version are you running?

---

### Post by drs305 on 2010-10-02
gnome-terminal **2.32.0** on Lucid 64.

However, on gnome-terminal **2.30.2**, Lucid 32, I don't even have an option in Profiles to set the default size. I remember some posts about this about a week ago. At the time, I still had the terminal size option but others did not. Apparently after an update I've lost it too in 2.30.2

---

