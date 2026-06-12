---
title: "Multiple line commands"
date: 2009-09-05
forum: General Help
---

### Post by Robbyx on 2009-09-05
I often see long lists of terminal commands. Is there a way of copying and pasting the lot into terminal and let them run automatically?

---

### Post by fluffman86 on 2009-09-05
Usually you can.  A line break in a list of commands will often be like pressing Enter in terminal and running that command.  Or, you can copy & paste the commands onto a single line in a text editor and put "&&" between each command. So
```
sudo apt-get update && sudo apt-get upgrade
```
is the same as
```
sudo apt-get update
sudo apt-get upgrade
```

Also, to actually do the copy and pasting, you can copy from one program (like firefox or gedit) as normal, then right click and select paste.  Or, you can just highlight a command and middle click in terminal to paste.

---

### Post by Robbyx on 2009-09-05
Thanks. 

I wonder if someone has written a script that will copy the blocked items into memory, replace the LF with &&

---

### Post by defacto on 2009-09-05
Create a shell script ( .sh ).

---

### Post by Robbyx on 2009-09-05
> **defacto said:**
> Create a shell script ( .sh ).

That would be a good idea if I knew what I was doing. I need someone else to have done it.

---

### Post by Liolikas on 2009-09-05
If you copy paste:
```

sudo apt-get update
sudo apt-get upgrade

```
Into text file and save it and in properties or with chmod command make that file executable and run thet file commands will be executed one after other. Of course sh script is capable to do much more.

---

### Post by bodhi.zazen on 2009-09-05
> **fluffman86 said:**
> Usually you can.  A line break in a list of commands will often be like pressing Enter in terminal and running that command.  Or, you can copy & paste the commands onto a single line in a text editor and put "&&" between each command. So
```
sudo apt-get update && sudo apt-get upgrade
```is the same as
```
sudo apt-get update
sudo apt-get upgrade
```Also, to actually do the copy and pasting, you can copy from one program (like firefox or gedit) as normal, then right click and select paste.  Or, you can just highlight a command and middle click in terminal to paste.

No it is not.

for multiple command you have a number of options.

first you can break a line with a \

sudo apt-get install -y package1 ... package10

can be 

sudo apt-get intall -y package1 \
package2 ... package5 \
package6 ... package10

You can run multiple commands with ; , && , and ||

command1; command2 is the same as

command1
command2

command1 && command2
&& = and -> command 2 runs only if command 1 is successful. If command 1 exits with an error , command 2 will not run.

command1 || command2
|| = or -> command 2 will run only if command 1 fails

| is a pipe

command1 | command2 
The output of command1 is sent to command2

tee can also redirect output.

---

### Post by bodhi.zazen on 2009-09-05
> **Robbyx said:**
> That would be a good idea if I knew what I was doing. I need someone else to have done it.

Snell scripts are easy to start with.

They start with a "#!/bin/bash"

[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

