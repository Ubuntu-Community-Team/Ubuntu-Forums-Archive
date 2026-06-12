---
title: "Python saving programs."
date: 2010-04-11
forum: General Help
---

### Post by oleink on 2010-04-11
Hello,
I wanted to save a python program because I am reading byte of python and I went to save in !/usr/bin.  When I try to save in this folder I get this error "[Errno 13] Permission denied: 'usr/bin/helloworld.py'

---

### Post by The Cog on 2010-04-11
You need to borrow super-user rights to write to folders outside your home folder. You can do this with command-line commands pb prefixing the commadn with the word **sudo**, e.g.> sudo cp hello.py /usr/bin Or you can start a privileged file manager with the command **gksudo nautilus**. 
This reference should help explain why:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wojox on 2010-04-11
Create a /bin directory in your /home/oleink directory and save them in there. You can then add the path to your .bashrc file and call your scripts directly. :)

---

### Post by oleink on 2010-04-12
Ok thanks.  I granted access to myself via terminal but now i have new problem.  When you type (in python) helloworld.py shouldn't the program access that file?  I don't know how to get python to find my saved program:confused:

---

### Post by Mighty_Joe on 2010-04-12
> **oleink said:**
> When you type (in python) helloworld.py shouldn't the program access that file?  

No.  If you want to execute a Python script, type "python helloworld.py" at the command line (NOT in the interactive Python console).

---

### Post by blur xc on 2010-04-12
AFAIK- if you have the "#!/usr/bin/env python" in the first line of your program, you gave the program execute permissions, and it's in a path-ed directory, you should be able to run it just by typing in its filename at a bash prompt.  

BM

---

### Post by oleink on 2010-04-12
ok.ok. I got usr/bin both accessable but there is no directory named "python"

---

### Post by oleink on 2010-04-12
OK wow this shows how much of a newbie i am.  I didn't realize I needed to be in the directory in the terminal to use the program with python.  I feel like a moron haha THANKS GUYS!!!!!!:lolflag:

---

### Post by J V on 2010-04-12
You REALLY shoulden't give yourself permissions to the /usr/bin directory...

Make a ~/bin directory and use that instead...

Then you just open a terminal and type "cd bin" to get access to your programs...

---

### Post by oleink on 2010-04-12
Im using bin in my home folder

---

### Post by The Cog on 2010-04-14
> **oleink said:**
> Im using bin in my home folder

That is indeed the right way to do it. But you don't actually need to be in the folder to run the file - you just have to tell python where it is. This will do it for you:
**python /home/oleink/bin/helloworld.py**
but you can also use a short-cut representation for your home directory like this:
**python ~/bin/helloworld.py**

You can also make the helloworld.py executable and run it like any other program. Firstly, add a line to the first line of the script telling the OS how to run the program. Since it's a python program, the first line should look like this:
```
#!/usr/bin/python
```
Secondly, make the script executable. You can do this by right-clicking the file's icon and choosing properties/permissions, or in the command line: **chmod +x ~/bin/helloworld.py**

Then you an run the program directly with the command **~/bin/helloworld.py** .

---

### Post by oleink on 2010-04-14
Thanks its all good now

---

