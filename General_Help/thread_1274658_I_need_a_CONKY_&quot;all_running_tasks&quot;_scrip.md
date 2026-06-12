---
title: "I need a CONKY &quot;all running tasks&quot; script"
date: 2009-09-24
forum: General Help
---

### Post by trstncmpbll on 2009-09-24
im looking for a script to show all the running tasks and background programs, i want to see everything thats going on even if its sleeping, and i want it by its self on the bottom right of my desktop, heres a pic of my setup
thank you very much!
tristan
[IMG]http://img.photobucket.com/albums/v610/trstncmpbll/screenshot-2.jpg[/IMG]

---

### Post by Brandon Williams on 2009-09-25
If you're just looking for a listing of processes with a little bit of information about their state, then you don't need a script. Just use 'ps -e'. View the man page for ps to get more information about how it's used and arguments that control the output format.

---

### Post by trstncmpbll on 2009-09-25
hey thanks for the response, the only thing is i want this to be in my desktop background at all times to view like conky and i need it to display all sleeping activity as well.
any thoughts

---

### Post by Brandon Williams on 2009-09-25
'ps -e' displays all processes, include those that are sleeping or defunct. It's just a matter of telling conky how often to run the command.

FWIW, on my system, this isn't very useful, since it will almost always require more lines to display than are available to conky on the screen. You may need to filter the listing somehow in order to ensure that it doesn't overflow the screen. If that's true, then you might need a script after all.

---

### Post by trstncmpbll on 2009-09-25
ok so i have everything going the way i want it to but now how do i get .conkyrc2 to start when the computer boots automatically. because of right now i have to run "conky & conky -c ~/.conkyrc2" to boot both of them

---

### Post by trstncmpbll on 2009-09-25
got it under .config openbox startup.sh

---

