---
title: "Sage math program"
date: 2010-04-19
forum: General Help
---

### Post by Legion81 on 2010-04-19
I just installed Linux 2 days ago, so I'm not too familiar with it yet. I downloaded a program called "Sage" with the terminal and it appears to have installed. I used "sudo apt-get install sagemath" or something similar (copied what the terminal suggested). I tried to open the program with alt+F2 and typing "sage", but nothing happened. I typed "sage" into the terminal and got a product description and a couple options (notebook or license). I entered a password for the "admin" user but then it took me to a website "http://localhost:8001" where it said "guest" could not log in as admin.

I can't figure out how to run the program. Everytime I type in "sage" now (with sudo or not) I get an error about "another twistd server is running". Does Sage only work online or something? I was under the impression that it was a program that could open on your computer like Mathematica or Matlab does. This may be silly, but I can't find how to open the program.

Thanks in advance.

---

### Post by luigi_mb on 2010-04-19
> **Legion81 said:**
> I just installed Linux 2 days ago, so I'm not too familiar with it yet. I downloaded a program called "Sage" with the terminal and it appears to have installed. I used "sudo apt-get install sagemath" or something similar (copied what the terminal suggested). I tried to open the program with alt+F2 and typing "sage", but nothing happened. I typed "sage" into the terminal and got a product description and a couple options (notebook or license). I entered a password for the "admin" user but then it took me to a website "http://localhost:8001" where it said "guest" could not log in as admin.

I can't figure out how to run the program. Everytime I type in "sage" now (with sudo or not) I get an error about "another twistd server is running". Does Sage only work online or something? I was under the impression that it was a program that could open on your computer like Mathematica or Matlab does. This may be silly, but I can't find how to open the program.

Thanks in advance.

Start sage as you did. Then in the sage console type "notebook()" (without the quotation marks). This will open a tab in your default browser. Then you can log in, etc. 

To exit from the sage shell just type "quit" (without the quotation marks).

/luigi

---

