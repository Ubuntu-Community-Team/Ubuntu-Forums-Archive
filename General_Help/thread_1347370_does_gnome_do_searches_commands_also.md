---
title: "does gnome do searches commands also?"
date: 2009-12-06
forum: General Help
---

### Post by roozbeh on 2009-12-06
I have installed gnome do and also lots of its plugins and i like it.

but for example in default run application (dont know the name,alt+f2) if i type add-a then it finds the rest (add-apt-repository) but this doesnt happend to me even when typing add-apt-reposi in gnome do.

is this normal or not?


tnx

---

### Post by VCoolio on 2009-12-06
I think gnome-do doesn't autocomplete the whole command database, only those where a launcher exists. Try to create a .desktop file in ~/.local/share/applications for add-apt-repository, then restart gnome-do and try again. 
But add-apt-repository needs a password and also the variable of the repo you're going to add. I think it would be better to create a command launcher that pops up a zenity entry window to enter your repository and then runs gksu add-apt-repository on that. Like so:

gksu add-apt-repository $(zenity --entry --text "Enter repository:")

You'll miss all output though, so no feedback on failure or success. I'd say just use the terminal or the software sources application (software-properties-gtk). Gnome-do should autocomplete the latter when you start typing 'software sources'.

---

