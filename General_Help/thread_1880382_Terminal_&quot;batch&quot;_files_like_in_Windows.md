---
title: "Terminal &quot;batch&quot; files like in Windows"
date: 2011-11-13
forum: General Help
---

### Post by Uchiha_Kori on 2011-11-13
Hello all.

I have recently converted from Windows 7 to Ubuntu. I am very pleased with it. I was dual booting, but decided to completely erase Windows and install Ubuntu. 

I am very interested in learning about the Terminal and the features of the CLI (Command Line Interface). I have already looked up several command lines and code. However, something I cannot find is how to make a "batch" file in Ubuntu. In Windows, you can open Notepad, typed a command line, then save the file as a .bat  file. After creating the .bat file, you can double click it, and the commands are ran just as if they were typed in the Command Prompt.

Is there a way I can open a word app in Ubuntu, type a terminal command, save it, then double click it and the code runs in terminal just like a batch file? -Thanks, Kori

---

### Post by eivindsm on 2011-11-13
What you describe here is probably the number one reason why people use linux based systems in the first place! There are plenty of editors around: emacs, vi, pico, nano, gedit+++. 

You need to decide what script interpretor to use, iow what language to use. Your shell is most probably bash, so you could start writing bash-scripts. Other popular alternatives python, perl, awk ++

Before you can run the script you'll need to make your text file executable. >chmod u+x filename
To run the script >./filename

Good luck!

---

### Post by llamabr on 2011-11-13
Right.  If you give us an example of what you're trying to do, someone can write up some sample code to get you going.

---

### Post by Lars Noodén on 2011-11-13
What you are asking about is called shell scripting.

Here are three links to get started with the shell:

[list]
[*][http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[*][http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[*][http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[/list]

Don't think of them as "commands" but as special programs that do one thing very well and that can be chained together.

---

### Post by The Cog on 2011-11-13
The procedure is much the same as doing batch files in windows. You need to use a text editor such as gedit or nano rather than a document editor, but that's true in windows too - the script must be a text file.

The difference is in how the OS knows it's a batch file. In windows, you call it something.bat. In Linux, you can give it any name you like, but you have to do the following two things:

1: The first line should start with
```
#!/bin/bash
```which tells Linux to use the bash command interpreter on the file. Scripts written in different languages such as python or perl will name their own interpreters on that first line of the script.

2: The script must be marked as executable. In linux, this is a file property much like the read-only property. You can set this with a command like **chmod +x filename** or can right-click the file and set the property in your graphical file manager.

Beyond what I said here, you will find the links that others have posted very informative.

---

### Post by Uchiha_Kori on 2011-11-13
Thank you all for your replies and help. I am very new, but very willing to learn and have fun doing it. Lars, that is some great reference material, I really appreciate it. So it's programming, yes? Like C++ and Java?

---

### Post by JKyleOKC on 2011-11-13
And here are a couple of trivial samples to show you the similarities and the differences:

Hello.bat (for Windows):
```

rem This is a simple batch file
type "Hello, world."

```
Hello (for Linux)
```

#!/bin/bat
# This is a simple shell script
echo "Hello, world."

```
Both do exactly the same thing when executed at a command line prompt in the appropriate system: display "Hello, world." and then return to the prompt level.

However the specific commands on each line are different. The links already cited in this thread will tell you about the specific commands in which you're interested for any specific task. You'll find that the shell scripts have many more things to choose from, and many more options for each command. When I'm creating a script for a new task, I first try out a line at a command prompt to be certain it does what I want, and then copy it into the script. It's much easier to do it this way than it is to write an entire script, then run it, and try to determine which line is making it go awry!

---

### Post by eivindsm on 2011-11-13
Hi Kori

most of the answers here promote bash scripting. From your reply it seems you're already familiar to object oriented programming in java and c++. If this is the case I would advice you to go for an object oriented scripting language such as python. Bash scripting is efficient, but quit low level. With python f.instance you will find that almost everything you need is coded and made available on the net by others; plug and play.

Just a thought.
E

---

### Post by JKyleOKC on 2011-11-13
eivindsm, what you say is true, but the OP originally asked specifically for the Linux equivalent of Windows "bat" files -- and that would be bash scripts, in *buntu where bash is the default shell. While perl and python scripts do have much more in the way of libraries and pre-built components available, they're more akin to programming for Windows using Visual Basic or Delphi, requiring some knowledge of the available libraries, and are not amenable to line-by-line testing from a separate command-line window.

Just look at how much of the code provided in the box actually is made up of shell scripts! Using them is much more consistent with the original Unix philosophy, IMO, than is the creation of small o-o packages -- but one of the great things about Linux is the great number of ways it offers us to shoot ourselves in the feet! :)

---

