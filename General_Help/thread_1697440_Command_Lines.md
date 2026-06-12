---
title: "Command Lines"
date: 2011-02-28
forum: General Help
---

### Post by ajcurran16 on 2011-02-28
I'm new to Ubuntu, I just switched over from Windows and don't know very many command lines to use in the terminal.

Can you guys just post some command lines and give a brief description of what they do?

---

### Post by Smart Viking on 2011-02-28
[http://linuxcommand.org/](http://linuxcommand.org/)
That is a nice tutorial to learn the basics of the bash shell.
Here are some commands:


download and install the program "frozen-bubble"
"sudo" means that this command should be runned as the root user, that is because when you install software, the executable files is placed in directories outside your home directory which you don't have write permission in. The reason they are placed there is because when other users are on the computer, they can play frozen-bubble as well. "apt-get" is the name of the program that does all the hard work, the reason we can just use "apt-get" instead of the whole path to the executable file is because it is located in one of the directories in the $PATH variable(run "echo $PATH" to see what directories are in your path.). "install" and "frozen-bubble" are both "arguments" to the "apt-get" program. The reason it takes arguments is because the program is designed to do many differen't things, so the first argument we pass to it is "install" to specify that we want to install a package(program), as opposed to removing a package, and the we passed  "frozen-bubble" as argument, so apt-get knows what to install. The reason why apt-get is smart enough to find out where to download the program from is because "frozen-bubble" is associated with an URL by the package manager.
```
sudo apt-get install frozen-bubble
```This will dump all the text from a text file into the terminal. "cat" is the program, "file.txt" is the argument we pass.
```
cat file.txt
```And so on.

---

### Post by Iowan on 2011-02-28
Here is another link:
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by ajcurran16 on 2011-02-28
Thanks for the links guys, I'll check them out when I get home.

---

