---
title: "Computer Janitor? (Ubuntu 9.10)"
date: 2010-03-26
forum: General Help
---

### Post by trixa_13 on 2010-03-26
I installed Computer Janitor and it has some packages that can be removed already but, when I clicked on "Do Selected Tasks", a dialogue box showed up. It says:

"You have chosen to remove 13 software packages. Removing packages that are still needed can cause errors."

I do not know if I will remove them or not. But, when I click on each package it says that:

"Package was installed because another package required it, but now nothing requires it anymore."

What shall I do?

[U][COLOR=Red][B]SOLVED!
[/B]I removed them already and nothing happened. :)[/COLOR]
[/U]

---

### Post by mike555 on 2010-03-26
I hosed my system using Janitor before , now I uninstall it first thing .......... you might want to error on the side of caution........

---

### Post by ubunterooster on 2010-03-26
Remove it :) 

Like it says, "nothing requires it aany more"

---

### Post by trixa_13 on 2010-03-26
> **ubunterooster said:**
> Remove it :) 

Like it says, "nothing requires it aany more"


But what if after removing them, I'll get an error. How will I get them back? It's only a "what if". :confused:

---

### Post by trixa_13 on 2010-03-26
> **mike555 said:**
> I hosed my system using Janitor before , now I uninstall it first thing .......... you might want to error on the side of caution........


Um... What do you mean?

---

### Post by ubunterooster on 2010-03-26
@trixa: "what if..." That's why we keep backups; just in case

"what do you mean?" He had a bad experience with the program

Could you list the items to be deleted?

---

### Post by QIII on 2010-03-26
Compter Janitor is ... how shall I say this in a politically appropriate way... a turd.

No offense meant to those who develop it.  But it has a habit of removing things on which other things depend.  Sometimes it can bork your entire system.

Just leave well enough alone.  Those excess applications will not bother you if you don't bother them.

---

### Post by trixa_13 on 2010-03-26
> **ubunterooster said:**
> @trixa: "what if..." That's why we keep backups; just in case

"what do you mean?" He had a bad experience with the program

Could you list the items to be deleted?

Ok. Here is the list.

_Under UNUSED:_
freeglut3
gnome-icon-theme-gartoon-redux
kdelibs-data
libblas3gf
libconfig-tiny-perl
libgfortran3
liblapack3gf
liblua50
liblualib50
libsdl-ttf2.0-0
python-numpy
python-opengl
python-pygame


_Under OPTIMIZE:_
/etc/apparmor.d/usr.bin.firefox-3.5.dpkg-old

---

### Post by ubunterooster on 2010-03-26
No unused programs are bloating system down. So while it appears they do not need to be there, there is no need to fix that which is not causing problems

---

