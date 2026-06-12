---
title: "How do you tell between a packing bug and an app bug? (We're supposed to know?!)"
date: 2010-08-13
forum: General Help
---

### Post by Ubuntiac on 2010-08-13
How on Earth can you tell the difference between a packaging bug and a bug in the software? I ask because Kubuntu.org says - on it's page for upgrading to KDE 4.5:

> Bugs in packaging should be reported to kubuntu-ppa on Launchpad. Bugs in the software to KDE.

Now I don't know where to file *any* bug! :(

---

### Post by gzarkadas on 2010-08-13
Bugs in packaging typically have to do with the package's installation and with supporting scripts and files, such as cron jobs, desktop menus and launchers, configuration files such as those in /etc/default, init scripts -if the package includes a service-, etc.

Bugs in applications typically have to do with running the application, such as a core dump, a displaced graphical element in its GUI, a wrong result in a calculation, etc.

There is certainly a grey line in between; if one can't decide on his/her own, then the best strategy might be to report first to kubuntu-ppa and let the people there examine it and decide the bug's fate.

---

### Post by Ubuntiac on 2010-08-13
Thanks gzarkadas,

That gives me a good place to start! I wonder who I'd  bug to add some kind of description like that to the release statements... Seems to me that most people would have no idea and be put off reporting without asking here like I did... :(

I'm guessing, probably The Riddler, himself. :-k

---

