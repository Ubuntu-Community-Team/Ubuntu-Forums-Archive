---
title: "How to start the launcher with a terminal comand?"
date: 2010-06-03
forum: General Help
---

### Post by elidoperezmd on 2010-06-03
Hi all...

I just made and launcher, and im interested in starting it using the terminal, how do i do that?

thanks for the help/replies/time

---

### Post by elidoperezmd on 2010-06-03
well i know i can start the terminal, go into the folder where the laucnher is and type the name...that will get it going.... what i mean is launching it as any other app...

for example when i hit amarok...amarok starts
thats what i want with this launcher, not having to go into the folder and launching it from wherever

---

### Post by elidoperezmd on 2010-06-03
huh??

---

### Post by xolot1 on 2010-06-04
Walk us through the use case one more time, please.

From what I understand, you have a program installed and you'd like an easy way to run it. 
Are you trying to run it from the desktop, or from the terminal?

If its from the desktop, as you said, you can create a launcher for it. The target is most likely /usr/bin/<program>, although this is application specific. If you need details, this is a good place to ask.

If its from the terminal, the program is most likely installed already. You should be able to launch it by typing its name into the terminal window. Try typing a few letters of the name, then pressing tab for auto-completion. If the program you are looking for is not listed, the executable is not found within this system PATH. This means the computer doesn't know where to find it. If this is the problem, come back here with details and we can help you out.

---

### Post by jerome1232 on 2010-06-04
Let's say the command you ran is coolprogram.bin

Let's also say coolprogram.bin is in /usr/local/games/ and you have to run it from within that folder.

What you would usually do is create a launcher script that cd's into that directory, then executes the program.

an example launcher script
```
#!/bin/sh
cd /usr/local/games
./coolprogram.bin
exit 0
```

Right click the launcher script, set it as executable. Then create a panel launcher or menu launcher and set your launcher script as the program to run.

Hopefully I make some sense.

---

