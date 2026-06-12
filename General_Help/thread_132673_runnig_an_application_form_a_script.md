---
title: "runnig an application form a script"
date: 2006-02-18
forum: General Help
---

### Post by tikal26 on 2006-02-18
Hey:
I run some of my applications from scripts but now I am running into some problems when trying to run a script from a panel button. the program is from processing.org I set up the button from the pannel give it a name and put the path in the executable, but when I press the button nothing happens any idea what might be wrong. I just run many of this things like that and it is becoming a pain to use the comman line everytime. Another application that I run like that is flock

---

### Post by Adrian on 2006-02-18
[QUOTE=tikal26]Hey:
I run some of my applications from scripts but now I am running into some problems when trying to run a script from a panel button. the program is from processing.org I set up the button from the pannel give it a name and put the path in the executable, but when I press the button nothing happens any idea what might be wrong. I just run many of this things like that and it is becoming a pain to use the comman line everytime. Another application that I run like that is flock[/QUOTE]

There should be no problem launching a script from a panel button. I just made a test script and it was executed properly.

Are you sure that your script is executable?
Have you tried running it from the terminal?

---

### Post by tikal26 on 2006-02-18
yeah I ran both of them from a terminal and I have no problem the problem is when I try it to run it from a button panel this is what I do
right click on the panel
Panel Menu
Add application to Panel
Add Non-kde application
Put a name under Button tile
Under executable I put the path to the script but no luck when I press the button
maybe I am doing something wrong

---

### Post by Adrian on 2006-02-18
[QUOTE=tikal26]yeah I ran both of them from a terminal and I have no problem the problem is when I try it to run it from a button panel this is what I do
right click on the panel
Panel Menu
Add application to Panel
Add Non-kde application
Put a name under Button tile
Under executable I put the path to the script but no luck when I press the button
maybe I am doing something wrong[/QUOTE]

Sounds correct to me. I did the same thing, and it works for me. Strange.

What happens if you check the "Run in a terminal window" checkbox? Does that give you any output?

---

### Post by tikal26 on 2006-02-18
here is the error that I get when trying to open on a terminal
Konsole is unable to oprn PTY (pseudo teletype).
It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write acces to PTY devices. That is for processing and for the flock button I get a   konsole but nothing happens and then it just disapears

---

### Post by Adrian on 2006-02-18
[QUOTE=tikal26]here is the error that I get when trying to open on a terminal
Konsole is unable to oprn PTY (pseudo teletype).
It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write acces to PTY devices. That is for processing and for the flock button I get a   konsole but nothing happens and then it just disapears[/QUOTE]

Well your first error tells us that you actually managed to run the script, so that is not the problem. I don't really know why you get that error though, since you have been able to execute it in a Konsole manually.

Regarding the second error, my best advice is to check the path again (copy the the location of the program and paste it in a Konsole to see if it REALLY is correct).

There are plenty of experienced users around here, and I'm sure that someone can find a solution for you.

---

