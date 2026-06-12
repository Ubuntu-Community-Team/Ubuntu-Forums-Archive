---
title: "make key switch permanent"
date: 2012-07-22
forum: General Help
---

### Post by chapra on 2012-07-22
Hi, I have been trying to remap two keys that are in the wrong place on my dell laptop. The right control and the menu key are switched on the dell laptop. I know the commands, but I can't make it permanent upon reboot.

In order to switch the keys, I have to enter:

xmodmap -e "keycode 105 = Menu"
xmodmap -e "keycode 135 = Control_R"
xmodmap -e "add Control = Control_R"
xmodmap -e "remove Control = Menu"

every time I boot up.  I have tried placing these commands in an .Xmodmap file, but it has no effect.

Chapra

---

### Post by Paddy Landau on 2012-07-23
Put those commands into a file called [FONT="Lucida Console"].profile[/FONT] in your home folder.

---

### Post by chapra on 2012-07-24
> **Paddy Landau said:**
> Put those commands into a file called [FONT=Lucida Console].profile[/FONT] in your home folder.

That did the trick!  Thanks a lot.


Chapra

---

### Post by Paddy Landau on 2012-07-25
> **chapra said:**
> That did the trick!
Excellent.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---

