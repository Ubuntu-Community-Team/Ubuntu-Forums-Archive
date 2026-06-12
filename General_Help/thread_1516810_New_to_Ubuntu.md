---
title: "New to Ubuntu"
date: 2010-06-24
forum: General Help
---

### Post by kustrle on 2010-06-24
So, I recently installed Ubuntu and I'm experiencing two problems.
1) Without graphic driver (which I am able to activate under 'Hardware drivers' or sth like that) I don't see screen where ubuntu is loading correctly and when I try to shut down Ubuntu I end at strange screen + computer doesn't shut down (so I have to do it by holding power button - which isn't really computer friendly...) If I activate driver my visual effects are set to 'None' and when I try to set them either to Normal or Best it says that Ubuntu was unable to do this... My graphic card is ATI Mobility Radeon HD 3400 Series
2) When I try to open .exe file that run a Windows program using Wine, I first see loading mouse cursor for some time (like 10-30 sec) then simply nothing happens. Same goes when I try to instal TeamSpeak 3 (which is .run file) using terminal. So, I set it's permissions so it can execute as program, I double click it, open in terminal, follow steps in terminal (accepting license) then when I accept license I see some text in terminal (for like 1 sec) then terminal close and again - nothing else happens even after 5 minutes of waiting.

So, probably I didn't provide enough info, mostly because idk what else you want to know. Fell free to ask. And thanks for any help!
~Kustrle

---

### Post by Woody1987 on 2010-06-24
1, install the driver, then in a terminal enter: sudo aticonfig --initial. Then reboot. This may fix your problem.

2, open a terminal, CD to the directory containing the exe and enter: wine filename.exe. This should show an output in the terminal displaying any errors that may occur. Do the same with .run file, but instead of wine filename.run, enter: ./filename.run.

---

