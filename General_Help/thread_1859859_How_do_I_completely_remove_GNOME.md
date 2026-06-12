---
title: "How do I completely remove GNOME?"
date: 2011-10-14
forum: General Help
---

### Post by linuxuser12345 on 2011-10-14
Hi, I am running Ubuntu 11.10 Oneiric Ocelot, and I just installed The GNOME Desktop Environment, with extra components in the Ubuntu Software Center. I decided I do not like the changes to GNOME and I would like to stay with Unity. Is there a way I can easily *completely remove* the packages and add-ons I just installed?

---

### Post by sgage on 2011-10-14
> **linuxuser12345 said:**
> Hi, I am running Ubuntu 11.10 Oneiric Ocelot, and I just installed The GNOME Desktop Environment, with extra components in the Ubuntu Software Center. I decided I do not like the changes to GNOME and I would like to stay with Unity. Is there a way I can easily *completely remove* the packages and add-ons I just installed?

You don't want to remove Gnome, because Unity works as a UI shell "on top of" Gnome. I'm guessing you want to remove the Gnome Shell (I prefer it over Unity, personally, but whatever floats your boat!)

```
sudo apt-get purge gnome-shell
```

That will probably leave a lot of auto-removable packages, so you may want to 

```
sudo apt-get autoremove
```

That should do it.

---

### Post by linuxuser12345 on 2011-10-15
Thank you. I just did a complete hard drive format, instead.

---

### Post by wi0 on 2011-10-15
What sgage was getting at is that if you use Unity, you have to have Gnome behind the scenes. But as long as you have your system working the way you wanted...

---

### Post by detoam on 2012-03-20
I used sudo apt-get purge gnome*.

---

