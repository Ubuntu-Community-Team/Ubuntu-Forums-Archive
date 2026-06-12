---
title: "How do I run /home/me/myscript.sh as just myscript from terminal"
date: 2011-12-25
forum: General Help
---

### Post by mmonkeh on 2011-12-25
I have a script that I currently run by typing in /home/me/myscript.sh into the terminal but I want to be able to run it just by typing myscript into the terminal. 

I want this:
matt@matt-hp:/$ myscript
to do the same thing as this:
matt@matt-hp:/$ /home/me/myscript.sh

Any help is greatly appreciated, thanks in advance!

---

### Post by mcduck on 2011-12-25
The scipt has to be in a directory that's defined in your path.

Create a directory ~/bin, and then move the script there (or make a symbolic link there). (You'll have to log out and back after creating the directory, and it'll get detected and added to your path automatically).

Alternatively you could just add the script's current location into your path, but I'd say using ~/bin is simpler and of course easier if you create more scripts in future...

```
mkdir ~/bin
mv ~/myscript.sh ~/bin/myscript
```
...and next time you log in you can just run "myscript" in a terminal. :)

---

### Post by mmonkeh on 2011-12-25
Worked perfectly, thanks!! :)

---

