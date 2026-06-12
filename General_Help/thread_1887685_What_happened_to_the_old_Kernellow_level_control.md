---
title: "What happened to the old Kernel/low level control?"
date: 2011-11-27
forum: General Help
---

### Post by scu-ba-de-buntu on 2011-11-27
FirstClass, WebCT, Blackboard,Flash, various games, etc. all tend to crash, but I don't think holding a power button for a hard shutdown is really a proper solution. This is not machine specific except that it happens more often on machines that are not high specs.
I remember years ago, it was possible to reboot with just a couple of buttons such as control-alt-backspace. Slackware used to be really good about this. You could always Control-alt-del or alt-F(x) to a terminal or process list. Now it seems that some programs are able to either block this or fail to accommodate. For example if running a game and it crashes in fullscreen, if the programmers have yet to add Xwindowing interrupts, nothing happens. What happened to keyboard-level control? Is there a place to vote for this back? Or maybe a IfIAmAtMyComputerIWantToHaveFullControl.DEB package? I joke, but seriously what happened? Sure I could reboot my machine anytime this crap happens, but why chance file system and hardware errors when I should easily be able to terminate broken processes.

---

### Post by searchfgold6789 on 2011-11-27
There are a couple things you can try:

[LIST]
[*]Ctrl-C, especially for things running in the terminal.
[*]Ctrl-alt-f1, ctrl-alt-f2 .... ctrl-alt-f6: gets you to a terminal
[*]Alt-f4: exits the window
[*]You can try setting keyboard shortcuts for window management, power control and other things. The program for doing this depends on what variant you're using.
[/LIST]

---

### Post by conradin on 2012-09-30
I repackaged the new firstclass version 10.014 to install correctly. If you like, I heard of a program called "2ndClass" that helps rouge firstclass processes shutdown correctly.

---

