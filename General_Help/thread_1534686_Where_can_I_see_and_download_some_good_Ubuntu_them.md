---
title: "Where can I see and download some good Ubuntu themes?"
date: 2010-07-19
forum: General Help
---

### Post by justinsn95 on 2010-07-19
You know how there are all these different themes, for various windows OS's? Many of them are pretty wild, many are beautiful. So where can I see, and download such themes for ubuntu and kubuntu? I am interested in making the bottom taskbar look a little more modern, as well as the window borders and window control buttons.

---

### Post by cariboo on 2010-07-19
Have you tried [gnome-look]("http://gnome-look.org/") or [kde-look]("http://kde-look.org/")?

Beware of .debs on either site.

---

### Post by Rubi1200 on 2010-07-19
> **cariboo907 said:**
> Beware of .debs on either site.

+1

Also, if you open Synaptic Package Manager and search for > themes you will also find additional things you could install. Maybe not quite as exciting as some of the ones in the links provided above but nonetheless...

---

### Post by justinsn95 on 2010-07-20
How do you do search for themes on synaptic package manager? "sudo apt get- themes"? If that is not the exact command line please let me know.

---

### Post by Vaphell on 2010-07-20
apt-cache search <keyword>, sudo not needed, then if you find that thing you want, sudo apt-get install <packagename>

---

### Post by WorMzy on 2010-07-20
> **justinsn95 said:**
> How do you do search for themes on synaptic package manager? "sudo apt get- themes"? If that is not the exact command line please let me know.

You're confusing synaptic (which is the GUI application) with apt-get (which is the command line application). To search Synaptic, open it from System -> Administration -> Synaptic Package Manager, and type your search term into the textbox on the top right of the window. To search apt, follow Vaphell's instructions above.

---

### Post by justinsn95 on 2010-08-12
> **WorMzy said:**
> You're confusing synaptic (which is the GUI application) with apt-get (which is the command line application). To search Synaptic, open it from System -> Administration -> Synaptic Package Manager, and type your search term into the textbox on the top right of the window. To search apt, follow Vaphell's instructions above.

So the Synaptic Package manager, and the terminal, both share the exact same repositories?

---

### Post by WorMzy on 2010-08-12
Yes, Synaptic is just a front-end to apt, so they have the same repositories.

---

