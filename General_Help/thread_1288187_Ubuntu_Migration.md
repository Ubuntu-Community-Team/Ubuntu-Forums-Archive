---
title: "Ubuntu Migration?"
date: 2009-10-11
forum: General Help
---

### Post by Lamez on 2009-10-11
So I was wondering, once I download 9.10 and install it. Will I be able to migrate all the data from 9.04 to the new installation? Data as in, wallpaper, settings, information, etc.

---

### Post by MelDJ on 2009-10-11
you can just update 9.04 to 9.10 and keep everything

---

### Post by Lamez on 2009-10-11
how would I do that?

---

### Post by MelDJ on 2009-10-11
go to system- administration- software sources. then enter your password. under the updates tab, you will see release upgrade. change it from long term support releases only to normal releases. this changes the update manager to notify you everytime a new version of ubuntu comes up and lets you update ubuntu to its newest version every 6 months. the former choice only prompts you to upgrade when the LTS version comes up.

---

### Post by bruno9779 on 2009-10-11
After the actual release of Karmic at the end of the month:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

I also usually run the following to check that everything went well:

```
sudo apt-get -f install
sudo dpkg --configure -a
```

PS: The final release is due October 29th. I advise you to wait till then unless you are sure of what you are doing

---

### Post by Lamez on 2009-10-11
Thanks guys!

---

