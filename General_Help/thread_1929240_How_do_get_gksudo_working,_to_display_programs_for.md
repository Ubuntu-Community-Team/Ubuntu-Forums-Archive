---
title: "How do get gksudo working, to display programs for a different user?"
date: 2012-02-21
forum: General Help
---

### Post by ut_nubu on 2012-02-21
Hi,

If I run the command: gksudo -u user2 gedit
I will get the error message 
'Gtk-WARNING **: cannot open display: :0.0'

However, if I run the command gksudo gedit, the program will be displayed.

If the command '[I]echo $DISPLAY' is executed, the terminal output is: ':0.0'

Could anyone please help to solve this issue? Thank you.
[/I]

---

### Post by ut_nubu on 2012-02-21
I applied the following
sudo xhost +local:user2

gedit will start now (although it takes very long), but gedit has no permission to write into /home/user2

'You do not have the permissions necessary to save the file.'

Any suggestion?

---

### Post by ut_nubu on 2012-02-21
Found this solution, which does the job for me.

ssh -X user2@localhost gedit

---

