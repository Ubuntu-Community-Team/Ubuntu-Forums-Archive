---
title: "How to make a script that runs a mere two lines of code."
date: 2011-11-09
forum: General Help
---

### Post by 646260 on 2011-11-09
Hey I know this is just complete beginner talk, but it would help to learn it some time I suppose.  I would like to make a script that can run these two lines of code:

cd ~/rsclient
java -Djava.class.path="$HOME/rsclient/client.jar" -Dcom.jagex.config=$'\x68\x74\x74\x70://\x77\x77\x77.runescape.\x63\x6f\x6d/k=3/l=en/jav_config\x2e\x77\x73' jagexappletviewer $HOME/rsclient/images

The code works, but I would like to know if I can make a script that can enter those to codes instead of typing the first line and copy/pasting the second line every time I want to run the program.  Thanks in advance.

---

### Post by carranty on 2011-11-09
I don't know about scripting, but you could use an 'alias' if its something you'll use often.  If you have two commands, command1 and command2 you can run them together on one line by placing a semicolon between them

[I]command1 ; command2

[/I]You can save this as an alias by using

[I]alias TEST='command1 ; command2'

[/I]where you can call TEST anything you like*. *To run the above you would only need to type TEST into the terminal.

If that works, you'll need to make it permanent by opening the .bashrc file in your home directory and pasting 

[I]alias TEST='command1 ; command2'

[/I]into it.

Hope that helps.

---

### Post by carranty on 2011-11-09
Also, you may want to add a third line at the end,

[I]cd -

[/I]This command will return you to the directory you were in before you ran the script/alias.

---

### Post by 646260 on 2011-11-09
Wow I feel stupid...the script was so simple.
#!/bin/bash
java -Djava.class.path="$HOME/rsclient/client.jar" -Dcom.jagex.config=$'\x68\x74\x74\x70://\x77\x77\x77.runescape.\x63\x6f\x6d/k=3/l=en/jav_config\x2e\x77\x73' jagexappletviewer $HOME/rsclient/images

Thanks though...I should've spent a little bit more time working on my own x).

---

### Post by alphaamanitin on 2011-11-09
An alternative to a script would be to type those commands, separated by a ";" into the terminal and hit enter once.  Then look the command up in the bash history, simply type 'history' into the terminal to find the commands number.  Find the number associated with the command you want, and when you next want to use the command type ```
!X
``` where X is the number of the command.

AlphaA

---

