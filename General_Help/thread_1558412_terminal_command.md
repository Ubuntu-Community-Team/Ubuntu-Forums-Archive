---
title: "terminal command"
date: 2010-08-22
forum: General Help
---

### Post by nishant29 on 2010-08-22
[IMG]file:///tmp/moz-screenshot.png[/IMG]
hi
i am new to ubuntu and using 10.04 and i have following problme that i used an application and when it is not completed this command prompt was lost "nishant@ubuntu:~$" as in the last line of my terminal how can i get back this command again without closing the terminal and opening the fresh one.

[COLOR=Red](Reading database ... 128043 files and directories currently installed.)
Unpacking cowsay (from .../cowsay_3.03-9.2_all.deb) ...
Processing triggers for man-db ...
Setting up cowsay (3.03-9.2) ...
nishant@ubuntu:~$ cowsay "i am speaking"
 _______________
< i am speaking >
 ---------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
nishant@ubuntu:~$ cowsay "i am handsome"
 _______________
< i am handsome >
 ---------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
nishant@ubuntu:~$ cowsay -f elephant"i am speaking too"[/COLOR]

---

### Post by d3v1150m471c on 2010-08-22
press up arrow while in terminal? not sure what you're asking

---

### Post by roger_1960 on 2010-08-22
You could open another tab?

---

### Post by nishant29 on 2010-08-22
i dont want to open new tab

---

### Post by nishant29 on 2010-08-22
[COLOR=Red][COLOR=Black]i want that following line to be displayed again after my last line in terminal which i had written before.. the up arrow gives nothing[/COLOR]
nishant@ubuntu:~$[/COLOR]

---

### Post by nishant29 on 2010-08-22
i dont want to open new tab

---

### Post by sikander3786 on 2010-08-22
After every successful command operation, the prompt should return to nishant@ubuntu:~$ for you.

If it is not showing up, means some operation is in progress. Ctrl + C will bring back the prompt for you in such a case but will also cancel the on going process.

I hope this is what you were looking for.

Regards.

---

### Post by jsstn on 2010-08-22
if your program has crashed, you can do ctrl-c in the terminal to terminate it and you will get your prompt back.
if the terminal just waits for some graphical program to stop before giving you the prompt back, you can type an ampersand [&] after you command input to make it run in the background: like gedit & (and if you don't want the program to quit if you exit the terminal: hohup gedit &).
maybe it helps if you tell us which program you try to run. is it cowsay?

---

### Post by WorMzy on 2010-08-22
> nishant@ubuntu:~$ cowsay -f _elephant"i am speaking too"_

The command isn't working because it's still expecting input, since you omitted a space between the elephant and the text.

As others have said, press Ctrl+C to cancel a command, then press the up arrow on your keyboard to recall the previous command, then add a space after "elephant" and re-execute the command.

---

### Post by nishant29 on 2010-08-22
[@sikander3786]("http://ubuntuforums.org/member.php?u=806649") thnx i m looking for that

---

### Post by nishant29 on 2010-08-22
[WorMzy]("http://ubuntuforums.org/member.php?u=1062896") thnx

nd yes that was cowsay

---

