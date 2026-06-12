---
title: "KDE Difference with Apt-get?"
date: 2006-04-10
forum: General Help
---

### Post by Mike_N on 2006-04-10
I was just wondering if their is any difference between installing Kubuntu or installing Ubuntu and then adding KDE?

Thanks, Mike

---

### Post by aysiu on 2006-04-10
[QUOTE=Mike_N]I was just wondering if their is any difference between installing Kubuntu or installing Ubuntu and then adding KDE?

Thanks, Mike[/QUOTE] Kubuntu = Ubuntu + KDE - Gnome.

---

### Post by Mike_N on 2006-04-10
So...

ubuntu + KDE

or

kubuntu + Gnome

is the same right?

---

### Post by N8MAN1068 on 2006-04-10
If you install Kubuntu straight from iso, you'll have the 'adept' package management system, which is different that synaptic. I didn't like it.

As I'm a creature of habit and often don't have time or patience to learn something new at home, I reinstalled Ubuntu and then downloaded the KDE packages.

At least this way, I can't switch over to Gnome again if I want.

---

### Post by aysiu on 2006-04-10
[QUOTE=Mike_N]So...

ubuntu + KDE

or

kubuntu + Gnome

is the same right?[/QUOTE] Yes.

---

### Post by Jonzo on 2006-04-10
I'm running GNOME right now..how can I switch to KDE?

sudo apt-get install KDE

Is that how?

---

### Post by aysiu on 2006-04-10
[QUOTE=Jonzo]I'm running GNOME right now..how can I switch to KDE?

sudo apt-get install KDE

Is that how?[/QUOTE] That's one way.

In case you decide later you don't like KDE, it's probably best to use *aptitude* instead of *apt-get*. *kde* is also not Ubuntu-specific (it has a lot more packages). *kubuntu-desktop* is Ubuntu's special set of KDE applications.

So you would probably do ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Log out. Select "Session" and "KDE" and log back in again.

---

### Post by jturnbul on 2006-04-10
[QUOTE=N8MAN1068]If you install Kubuntu straight from iso, you'll have the 'adept' package management system, which is different that synaptic. I didn't like it.

As I'm a creature of habit and often don't have time or patience to learn something new at home, I reinstalled Ubuntu and then downloaded the KDE packages.

At least this way, I can't switch over to Gnome again if I want.[/QUOTE]

you could also install Kubuntu, and then use adept to install synaptic afterwards.  Thats what I have set up.  I cant stand adept either.

---

### Post by N8MAN1068 on 2006-04-10
true
But i added the repositories for kde 3.5.1 so i could install that right off the bat

---

