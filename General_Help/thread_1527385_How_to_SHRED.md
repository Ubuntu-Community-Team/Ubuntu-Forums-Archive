---
title: "How to SHRED?"
date: 2010-07-09
forum: General Help
---

### Post by PDA1 on 2010-07-09
How do I use SHRED to delete an individual file?   I think you have to use SHRED in Terminal but I want to make sure I don't accidentally destroy my entire hard drive.

---

### Post by audiomick on 2010-07-09
Hallo.
I have never used shred, but it looks straightforward in the man page.
do
```
man shred
```
in a terminal to read that.

---

### Post by PDA1 on 2010-07-09
I can assure you unless someone knows how to use Shred I'll never enter any commands that look strange to me.  I'm no expert in Ubuntu but I'm certainly not going to enter Man Shred.

---

### Post by F.McC on 2010-07-09
'man shred' will bring up the man page of the program, the documentation and information on how to use the command. 

try 'man man' for more information.

---

### Post by philinux on 2010-07-09
> **PDA1 said:**
> I can assure you unless someone knows how to use Shred I'll never enter any commands that look strange to me.  I'm no expert in Ubuntu but I'm certainly not going to enter Man Shred.

Err. Man means man page = manual. i.e instructions on how to use shred.
You could have googled "man shred"

as in 

man apt-get
man ls

[http://linux.die.net/man/1/shred](http://linux.die.net/man/1/shred)

---

### Post by mbgaski on 2010-07-09
> **PDA1 said:**
> I can assure you unless someone knows how to use Shred I'll never enter any commands that look strange to me.  I'm no expert in Ubuntu but I'm certainly not going to enter Man Shred.

"man" brings up the man page - ie, the MANUAL on how to use a program.

Hence, "man shred" just tells you how to use it.

---

### Post by audiomick on 2010-07-09
> **PDA1 said:**
> I can assure you unless someone knows how to use Shred I'll never enter any commands that look strange to me.  I'm no expert in Ubuntu but I'm certainly not going to enter Man Shred.
Hallo.
```
man
```
anything is completely harmless. That is the command to open the manual page of programs.

a quote from here
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

> **"Man" and getting help**

 [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/alert.png[/IMG] **man *command***, **info *command*** and ***command* --help** are the most important tools at the command line. 
Nearly every command and application in Linux will have a man (manual) file, so finding them is as simple as typing **"man "command""** to bring up a longer manual entry for the specified command. For example, **"man mv"** will bring up the **mv** (Move) manual. 
Move up and down the man file with the arrow keys, and quit back to the command prompt with **"q"**. 
**"man man"** will bring up the manual entry for the **man** command, which is a good place to start! 

You are quite correct to not enter any commands in the terminal that you don't understand. :)

---

### Post by Zorgoth on 2010-07-09
man does *not* execute shred.  It merely displays a manual page describing how to use shred.  man is a seperate command and is not dangerous in any way.

I also believe there are extensions for nautilus that will allow you to shred; may be called "secure delete."  I do now know where they are.

---

