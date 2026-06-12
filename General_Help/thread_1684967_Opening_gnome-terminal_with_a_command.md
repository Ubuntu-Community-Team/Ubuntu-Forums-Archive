---
title: "Opening gnome-terminal with a command"
date: 2011-02-09
forum: General Help
---

### Post by Bre Ntt on 2011-02-09
I'm trying to make an application launcher that launches gnome-terminal with a terminal program running (a math program I want to be able to use as a calculator in a terminal). 

I tried 

gnome-terminal -e --theProgramCommand 

also gnome-terminal -x theProgramCommand

but that I get an error saying "can't open child process."  It is not an issue with the program in particular, because I tried it with other programs. 

And I can't just use the command "theProgramCommand" because this particular program seems to  run itself in the background, and doesn't open up the terminal interface, unless I actually run the program from a terminal.

If I click on the executable within a browser it gives me a dialog box asking if I want to run it in the terminal. So how does one make it run in a terminal from a command in the application launcher?


======
Nevermind, I missed the run in terminal" option on the application launcher. Solved it. Thanks anyway.

---

### Post by rvchari on 2011-02-09
can you create a desktop launcher shortcut and specify it to open with terminal ?

---

### Post by ZeljkoZgb on 2011-02-14
This is working for me, it opens terminal and executes command in terminal:

gnome-terminal -x bash -c "shell_command"

---

