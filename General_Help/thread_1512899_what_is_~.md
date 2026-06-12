---
title: "what is ~/?"
date: 2010-06-18
forum: General Help
---

### Post by heaver on 2010-06-18
i am supposed to paste some folder inside a another folder that is supposed to be on ~/.something...but i have no idea where do i go for this ~/ and do i use nautilus to copy the folder and paste it somewhere else?
thx in advance

---

### Post by new_tolinux on 2010-06-18
~/ is your home folder.

That means, if your username is for example heaver the ~/ folder specifies the same as /home/heaver/
So:
~/Desktop = /home/heaver/Desktop
~/Documents = /home/heaver/Documents
etc.

---

### Post by heaver on 2010-06-18
haha thanks =P

and what to u do when the folder is not there? could it be hidden?
cuz theres a dot before the name of the folder (~/.something)

---

### Post by warfacegod on 2010-06-18
~/ is a "shortcut" for the Terminal. It's basically the same as typing out: /home/yourusername/foldername. It tells the Terminal to go straight to a folder without having to type the entire path to it.

---

### Post by warfacegod on 2010-06-18
> **heaver said:**
> haha thanks =P

and what to u do when the folder is not there? could it be hidden?
cuz theres a dot before the name of the folder (~/.something)

Hidden doesn't matter. It will still work.

---

### Post by WorMzy on 2010-06-18
Folders and files with a dot at the start of their name are hidden by default in most file managers and terminal directory listing outputs. You can make them visible through use of a shortcut (in nautilus it's Ctrl+H), or through menus and preferences. The ls command can show hidden folders by using the -a option (ls -a), I'm not sure about the dir command, but I wouldn't recommend you use that anyway.

---

### Post by lisati on 2010-06-18
As others have pointed out, ~/ is a shortcut for your "home" folder, the folder/directory used in Linux and other Unix-like OSes for the individual user's data. There shouldn't be a dot in front of it.

./ is a shortcut for "this folder". It is often used for running programs stored in your current working directory, because unlike Windows, Linux-based systems by default don't always search for executable files in the current directory.

---

### Post by heaver on 2010-06-18
thanks a lot =P im rly bad at terminal stuff ..

---

### Post by new_tolinux on 2010-06-18
~/.something does point to /home/heaver/.something
Even if you don't see it by default you can enter that folder (cd ~/.something ) and use it.
Hidden folders are mostly used by applications to store your personal settings etc.

---

