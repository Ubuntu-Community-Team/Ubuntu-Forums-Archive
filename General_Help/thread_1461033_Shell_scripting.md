---
title: "Shell scripting"
date: 2010-04-23
forum: General Help
---

### Post by Ashish Asolkar on 2010-04-23
What is **shell scripting** ?
Help me Out..

Thanks.

---

### Post by Serpher on 2010-04-23
Shell scripting is just putting commands you would enter into your terminal each in one line. When the file is ran in the terminal by typing 'bash <file>' (Or 'sh' depending on the shell you want to use), it executes each line like it's own command. You can also use if statments. If you want to learn about it you could easily find a tutorial with google.

---

### Post by kanikilu on 2010-04-23
The **shell** is what most people would probably refer to as the command-line (CLI) or terminal. Their are several shells out there, but the Bourne Again SHell (BASH) is the standard. Scripts are basically sets of instructions like programs, but they are interpreted rather than compiled. I'm by no means an expert, the Linux Documentation Project is a good place to start:

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by quadproc on 2010-04-23
> **Ashish Asolkar said:**
> What is **shell scripting** ?

"Shell scripting" is writing a script to be executed in a shell.  A shell is a program which performs commands fed to it.  A script is usually a file which contains the things that you want the shell to do.  Here is a small example of a shell script:
```
cd /etc/X11
cat xorg.conf | grep "iver"
```This example first changes the working directory to /etc/X11 which is where the system expects to find information regarding its graphics hardware.  The next line executes the cat function which copies xorg.conf to the standard output; the | character causes the output from cat to be piped into grep; grep looks for strings which contain the string "iver" and displays those.

You could save this little two line script as a file and then you could simply type the name of that file every time that you want to execute these commands.

Shell scripts can be very complex.  In fact, it is readily possible to create a database system by writing a shell script.  I would not generally recommend that because you can get ready-made database systems but the example illustrates the power of the script.

quadproc

---

