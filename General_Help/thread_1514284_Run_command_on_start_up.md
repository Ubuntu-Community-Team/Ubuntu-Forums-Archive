---
title: "Run command on start up"
date: 2010-06-20
forum: General Help
---

### Post by seanelly on 2010-06-20
So I can run this command:```
[FONT=monospace]remind -z -k'gxmessage -title "reminder" %s &' ~/.reminders &[/FONT]
```from a terminal and then I'll get nice pop-up reminders from my remind calendar. How can I make this happen automatically upon start up? Much thanks.

---

### Post by kerry_s on 2010-06-20
look through your menus, there is a autostart program.

---

### Post by seanelly on 2010-06-21
While I did know that and your answer wasn't what I was looking for I do appreciate the reply. It promted me to investigate that direction more I found a solution that works for me. This is obvious, I imagine, to everyone, bt me, however, I'll explain the problem and what I did. Perhaps someone like me will find it useful or maybe someone can point out a better way to do this if there is one. 

I tried simply adding the desired code to a new command in xfce's session and startup > application autostart, but that didn't work. I then thought that maybe I need to put the code into a text file and make it executable. I added this to a new text file in my home directory:
```
#!/bin/sh
remind -z -k'gxmessage -title "reminder" %s &' ~/.reminders &^C
```From a terminal I then entered:
```
chmod +x <location of new text file>
```and that somehow made it executable. I can now edit the startup file that was made in ~/.config/autostart or make a new one from the settings manager and use the command:
```
./<new text file>
```
Look at that, I'm learning and figuring stuff out. :guitar: My wyrd entries now give me wonderful popup reminders via gxmessage.

---

### Post by kerry_s on 2010-06-21
sorry, i thought it was already in a executable file.

personal executables, create a folder named "bin"
put your executables(scripts) in there, then you can just use the name, careful not to name it something that exists in the system already.

bin is sourced at log in, so when you create it, it won't be active till your first log out & log in.

it's linux's little way of keeping things clean. :lolflag:

---

### Post by seanelly on 2010-06-21
Even better, thanks!

---

