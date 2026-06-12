---
title: "what happened to Ubuntu's dictionary program?"
date: 2011-06-18
forum: General Help
---

### Post by ki4jgt on 2011-06-18
What happened to Ubuntu's built in dictionary program? In the office category.

---

### Post by lisati on 2011-06-18
Hmmmm interesting... there's one there on my 11.04 installation's Application->Office menu. I also see there's a choice of dictionaries to install available through the software center.

---

### Post by coffeecat on 2011-06-18
> **lisati said:**
> Hmmmm interesting... there's one there on my 11.04 installation's Application->Office menu. I also see there's a choice of dictionaries to install available through the software center.

@lisati, are you sure you didn't install it yourself? There's no dictionary listed in my installed applications under Applications > Office in 11.04 Unity and a search for "dictionary" in the dash doesn't show it. I've logged back into the classic desktop (a first for this system! :)) and the dictionary is not in the Applications > Accessories menu where it used to be in Maverick and before, iirc. Nor in the Applications > Office menu either.

I'll log back into Unity and dig around a bit more.

---

### Post by ki4jgt on 2011-06-18
> **lisati said:**
> Hmmmm interesting... there's one there on my 11.04 installation's Application->Office menu. I also see there's a choice of dictionaries to install available through the software center.

But which one was installed on all the previous distros of Ubuntu, I've already checked the USC. The one Ubuntu had, is the one I'm interested in.

---

### Post by coffeecat on 2011-06-18
> **coffeecat said:**
> I'll log back into Unity and dig around a bit more.

> **ki4jgt said:**
> But which one was installed on all the previous distros of Ubuntu, I've already checked the USC. The one Ubuntu had, is the one I'm interested in.

I'm back in Unity and remembered that I had Maverick installed in a VM in Vbox. A quick check in that shows that the dictionary was in the Office menu, not Accessories (my memory was faulty), and that the package name was "gnome-dictionary". That is not installed in my 11.04 and I did not uninstall it so it can't have come as default. Anyway, I've now installed the package gnome-dictionary and it now appears if I right-click the Applications launcher icon > Office and works as well as in earlier versions of Ubuntu.

---

### Post by mc4man on 2011-06-18
There is a simple one included  - gnome-dictionary

---

### Post by ki4jgt on 2011-06-18
> **mc4man said:**
> There is a simple one included  - gnome-dictionary

It's no longer included. That was my question, what was it called.

---

### Post by donato roque on 2011-06-18
I am using ubuntu 11.04. To use gnome-dictionary (formerly comes default): use the Ubuntu Software Center and search for gnome-dictionary. If I'm not mistaken it comes bundled with baobab, the disk usage analyser.

I like a dedicated thesaurus myself along with the dictionary. I use Gaiksaurus, also available at the Ubuntu Software Center. 

Tip: I love my keyboard shortcuts. I like these two tools handy so I made them keyboard shortcuts. Go to Dash and open keyboard shortcuts. The location for the two should be /usr/bin/gnome-dictionary and /usr/bin/gaiksaurus. Use an appropriate shortcut like Cntrl+Shift+D.

---

