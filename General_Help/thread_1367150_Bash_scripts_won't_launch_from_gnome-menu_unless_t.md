---
title: "Bash scripts won't launch from gnome-menu unless they cd into target directory"
date: 2009-12-29
forum: General Help
---

### Post by dai_vernon on 2009-12-29
This is very odd, but whenever I make a launcher in gnome-menu or gnome-panel that launches a shell script, they will not work properly unless the script explicitly cd into the directory where the files that the script deal with are located.  These scripts work just fine when run manually in a terminal, and when executed by clicking them in nautilus, but for some reason gnome-menu and gnome-panel are special, and won't execute the scripts properly.

Is there something special about the gnome launching mechanism that requires modified scripts?  Is there something about my scripts that is missing?

---

### Post by victor.zamanian on 2009-12-29
Yes whenever you launch a program from the menu or panel, the default current directory will probably be the $HOME directory. Thus you will unfortunately have to explicitly change the directory.

You could change the launcher to run it in a terminal and then modify the script to print the current directory by just adding a line:

pwd
or
echo $PWD

to verify that the script's current directory is your $HOME directory.

---

### Post by pbrane on 2009-12-29
Whenever you write a script use full path names instead of assuming the current working directory. With that you can run the script from any directory.

---

