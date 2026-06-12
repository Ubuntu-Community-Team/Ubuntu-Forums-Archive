---
title: "run programs/commands without attachment to terminal?"
date: 2006-03-28
forum: General Help
---

### Post by jms830 on 2006-03-28
if i type a command into terminal, for example "gaim", then i cannot use the terminal until I close gaim. I know I can use alt+F2 for the run command, or open a new tab, but is there an option or something to run a command/program "detatched" from the terminal I'm using? just curious, it would be nice to know.

---

### Post by christhemonkey on 2006-03-28
I would also love this functionality, some programs you can put to background by pressing (i think) Ctrl+X, but this doesnt allways work.

---

### Post by engla on 2006-03-28
If you append **&** to the command, the program will be sent to the background and you can use the terminal for other things.

If you prefix the command with **nohup** the command will continue to run even if you close the terminal.

If you have an already running process, you can type **Ctrl-Z** to pause it, then **bg** to continue it in the background (frees the terminal) or **fg** to continue it in the foreground.

*A small, off-topic but cool thing: * You can pause any application, if you want it. Just use 'kill' as you normally would, but send the signal STOP: "kill -STOP 556" where 556 is the pid of the program. The program will be paused, use 0% cpu and it's windows won't redraw. This *can* be useful [but confusing] if you want to pause a heavy program for just a while. Continue the process by using 'kill -CONT 556'

---

### Post by pacman^ on 2006-03-28
Yes, there is an option. You run the command exactly the same way but put a & right after it. That makes the process independent and you can use the terminal or even close it after launching the desired program. 

Example: 

```

:~$ mozilla& 
:~$ 

```

Edit: Yikes! How fast are you really? I didn't think too long with that posting...

---

### Post by jms830 on 2006-03-28
cool, thanks. oh and the off subject tip is cool, for people who prefer the GUI way to do it, you can open your system monitor (ctrl+alt+delete thing) and right -click on a process to STOP and CONTINUE it :-D

---

### Post by engla on 2006-03-28
[QUOTE=jms830]cool, thanks. oh and the off subject tip is cool, for people who prefer the GUI way to do it, you can open your system monitor (ctrl+alt+delete thing) and right -click on a process to STOP and CONTINUE it :-D[/QUOTE]Ah, neat. Thanks for the reverse-tip.

---

