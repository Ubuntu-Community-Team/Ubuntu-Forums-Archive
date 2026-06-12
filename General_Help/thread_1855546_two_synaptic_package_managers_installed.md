---
title: "two synaptic package managers installed"
date: 2011-10-06
forum: General Help
---

### Post by doogiekd on 2011-10-06
hi, 

not sure if this is a big deal or not - but its weird and annoying:

last week i noticed that my synaptic package manager (spm) had changed to the one used by ubuntu. the clue was the "quick filter" box at the top of the screen. next to the quick filter box is the regular "serch" button found in lubuntu. both options work fine. i thought that the "quick filter" box was part of an update for lubuntu and ignored it.

then yesterday i tried adding synaptic package manager to the desktop panel and discovered that 2 spm's were listed when editing the application launch bar menu.

only one spm is listed in the main menu.

i added both spm's to the panel and tried to launch each of them separately.  

the first one launched normally and is the ubuntu style with the "quick filter" and serch button.

when launching the second spm a box appeared saying:

Starting without administrative privileges

You will not be able to apply any changes. But you can still export the marked changes or create a download script for them.

the spm then started and was the lubuntu spm - it did not include the "quick filter."

question: is this a problem? i really liked using the lubuntu spm without the quick filter option. is there any way to delete the ubuntu spm and just have the lubuntu spm with administrative privlages?

also, i confirmed the gnome was not installed accidentally.

k.

---

### Post by oldos2er on 2011-10-06
You should be able to just delete the launcher you don't need, right?

---

### Post by doogiekd on 2011-10-06
correct. 

the launcher only appears in the application launch editing box in panel.

i was wondering if having 2 spm's on my system could cause problems. also, not sure if the packages are the same in both the ubuntu and lubuntu spm.

---

### Post by oldos2er on 2011-10-06
You only have one Synaptic Package Manager; one launcher in Gnome and one in lxde. You should be able to edit the launcher options of either in the way you desire.

Every package manager front-end e.g. Software Center, Synaptic, apt-get, etc. accesses the same repositories (those in /etc/apt/sources.list and /etc/apt/sources.list.d/).

---

### Post by doogiekd on 2011-10-07
but the funny thing is i don't have gnome installed, only lubuntu/lxde.

so why is the gnome synaptic there?

and does this have the possibility of causing conflicts?

also, when adding both spm's to panel, only the gnome version will launch. the error box described above appears when i start the lubuntu/lxde version.

?

---

