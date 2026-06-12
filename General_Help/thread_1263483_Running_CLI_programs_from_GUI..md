---
title: "Running CLI programs from GUI."
date: 2009-09-11
forum: General Help
---

### Post by jwbrase on 2009-09-11
Is there any way to trigger the execution of a program in a terminal window from the GUI? For example, assume I have a program xyz.py. To run that program, I can always open a terminal window, cd to the program's folder, and type "python xyz.py", and the program will dump its output to the open terminal window. But if I browse to the program's folder in Nautilus and click on the program, nothing (visible) happens. I assume that the program does in fact run, but since there is no open terminal window for it to send its output to, the output gets dumped (figuratively speaking) to /dev/null. And since I don't get any output, I don't know for certain if the program actually runs. It could crash without me knowing it. So what I'd like to be able to do is configure things so that clicking "xyz.py" in nautilus will automatically launch a terminal window, which will in turn automatically run "python xyz.py". (Or, more generally, so that clicking on a program that sends output to the terminal opens a terminal window and runs the program)

Is there any way to do this, or am I wanting Linux to be too much like Windows?

---

### Post by dcstar on 2009-09-11
> **jwbrase said:**
> Is there any way to trigger the execution of a program in a terminal window from the GUI? For example, assume I have a program xyz.py. To run that program, I can always open a terminal window, cd to the program's folder, and type "python xyz.py", and the program will dump its output to the open terminal window. But if I browse to the program's folder in Nautilus and click on the program, nothing (visible) happens. I assume that the program does in fact run, but since there is no open terminal window for it to send its output to, the output gets dumped (figuratively speaking) to /dev/null. And since I don't get any output, I don't know for certain if the program actually runs. It could crash without me knowing it. So what I'd like to be able to do is configure things so that clicking "xyz.py" in nautilus will automatically launch a terminal window, which will in turn automatically run "python xyz.py". (Or, more generally, so that clicking on a program that sends output to the terminal opens a terminal window and runs the program)

Is there any way to do this, or am I wanting Linux to be too much like Windows?

Create a launcher of "Application in Terminal" type.

---

### Post by cak3 on 2009-09-11
You can set the file as executable, and then nautilus will notice that and ask you if you want to open it in a text editor or run it. You can either do that from the command line, by typing ```
chmod +x [filename]
``` or right clicking on it and opening properties, (in nautilus). Under the permissions tab, there is a checkbox to allow execution.

You do want to be sure the file has a proper shebang, since you aren't telling it what to run with. By that I mean (for the python example) the ```
#!/usr/bin/python
``` as the first line.

---

### Post by P4man on 2009-09-11
If you want a python program to keep the terminal open after it finishes, add this line at the end of the script:

raw_input("\n\nPress the enter key to exit.")

Then you can just double click it in nautilus (or use a launcher to launch it) without missing the output.

---

### Post by jwbrase on 2009-09-11
> **dcstar said:**
> Create a launcher of "Application in Terminal" type.

I can't seem to get this to work.

> **cak3 said:**
> You can set the file as executable, and then nautilus will notice that and ask you if you want to open it in a text editor or run it. You can either do that from the command line, by typing ```
chmod +x [filename]
``` or right clicking on it and opening properties, (in nautilus). Under the permissions tab, there is a checkbox to allow execution.

You do want to be sure the file has a proper shebang, since you aren't telling it what to run with. By that I mean (for the python example) the ```
#!/usr/bin/python
``` as the first line.

I'd already set it as executable. The shebang was my problem with getting it to run. I just got this laptop and had brought the python files in question over on my flash drive from a Windows machine. Now that I've fixed the shebang, it runs (I was able to confirm this by deleting an output file, then running the program and watching it recreate the file). However, I'm still not able to get it to output to a terminal window.

> **P4man said:**
> If you want a python program to keep the terminal open after it finishes, add this line at the end of the script:

raw_input("\n\nPress the enter key to exit.")

Then you can just double click it in nautilus (or use a launcher to launch it) without missing the output.

I tried adding that line, but it hasn't done anything. Double clicking in nautilus runs the script now that I have a proper shebang, but it doesn't open a terminal Window in the first place, so that line doesn't have a terminal window to keep open.

---

### Post by P4man on 2009-09-11
> **jwbrase said:**
> 
I tried adding that line, but it hasn't done anything. Double clicking in nautilus runs the script now that I have a proper shebang, but it doesn't open a terminal Window in the first place, so that line doesn't have a terminal window to keep open.

When you double click it, doesn't it ask you to run it in a terminal, run or edit ?

---

### Post by cak3 on 2009-09-11
When you double-click it, does it give the 'run in terminal' option? I think that should do what you want.

Edit: beat me to it

---

### Post by jwbrase on 2009-09-11
> **P4man said:**
> When you double click it, doesn't it ask you to run it in a terminal, run or edit ?

#-o

Wow. How did I miss that...

---

### Post by satyapraveen27 on 2009-09-22
Hai i am trying to call a clip program in GUI program....
ie., when we click the button in gui state then the clip program has to run and we should get the o/p.
can any one help me on this topic........
thanks in advance....

---

### Post by 3rdalbum on 2009-09-22
> **satyapraveen27 said:**
> Hai i am trying to call a clip program in GUI program....
ie., when we click the button in gui state then the clip program has to run and we should get the o/p.
can any one help me on this topic........
thanks in advance....

1. There are heaps of programs around that do this, and because this is Linux it's all open-source; have a look at some other programs and see how they do it.

2. I program in Python, and I use:

```
import commands
result = commands.getoutput("ps aux")

```

---

### Post by satyapraveen27 on 2009-10-08
hai.....
I working on both clips and wxpython and i am trying to take a sentence from clips and in that i am splitting each word and displaying those words as buttons in GUI using wxpython.....
I am not able to work out it can anyone post the program to my mailid.......(satyapraveen27@in.com)
can anyone say that is it possible to load-facts of other file and display those facts in the GUI state.....

---

