---
title: "Custom Application Launcher and Terminal command"
date: 2009-12-03
forum: General Help
---

### Post by sashaluda on 2009-12-03
Hi All.

I have a problem creating custom application launcher with cp (copy files) command.

Here is the example of working sh file:
-----
#!/bin/bash
cp /tmp/Flash* ~/Desktop/
-----
It copies currently viewed (in firefox) flash files to desktop successfully. To launch this file I have to perform right-mouse click on it-->open with-->sh.

Here is not working custom application launcher properties:

Type: Application in terminal
Name: Copy Flash
Command: cp /tmp/Flash* ~/Desktop/
Comment: Copy FLV files from TMP to Desktop

It would be nice if I could get rid of the sh file completely and use just Custom Application Launcher in one of my Drawers. That's why I don't want to try to run sh file from Drawer.

I think the solution is simple-- it would teach me how to use any terminal commands in application launchers.

Thanks in advance.
Sasha.

---

### Post by lloyd_b on 2009-12-03
The one real problem I see is that "*" - that's a shell wildcard, and without a shell running, it won't expand the way you'd expect (It'll try to copy a file literally named "/tmp/Flash*", rather than getting all Flash... files in the /tmp directory).

What you can do is tell it to run the 'cp' command within a shell.  Replace your command with "sh -c cp /tmp/Flash* ~/Desktop/" and see if that works the way you expect.

(Or "bash -c ...".  For this command, either 'sh' or 'bash' will work fine).

Lloyd B.

---

### Post by jocko on 2009-12-03
This works for me:
```
bash -c "cp /tmp/Flash* ~/Desktop/"
```

---

### Post by sashaluda on 2009-12-03
> **jocko said:**
> This works for me:
```
bash -c "cp /tmp/Flash* ~/Desktop/"
```

Thank you. It works indeed.
The last thing is  -- the terminal window that quickly appears when the command is executed.

I know -- it's inevitable if I use bash. I was impressed by the beauty of Linux launching console commands without opening one (I have custom application launcher with some dvd speed limiter - the console application and no terminal window appears! of course without bash prefix and not as terminal application)

I guess -- I'll survive...

P.S. Tried 
cp "/tmp/Flash* ~/Desktop/" 
and 
"cp /tmp/Flash* ~/Desktop/"
no luck... maybe there is a way to run bash minimized ...?

---

### Post by lloyd_b on 2009-12-03
Not familiar with Gnome, but```
**Type: Application in terminal**
Name: Copy Flash
Command: cp /tmp/Flash* ~/Desktop/
Comment: Copy FLV files from TMP to Desktop
```with a type of "Application in terminal" you'd pretty much expect it to run a terminal.

Is there just a plain "Application" type?

(I run Xubuntu, which uses the Xfce desktop, so I can't test it for myself.  Under Xfce, there's a checkbox in the configuration to specify whether to run in a terminal or not).

Lloyd B.

---

### Post by sashaluda on 2009-12-03
> **lloyd_b said:**
> The one real problem I see is that "*" - that's a shell wildcard, and without a shell running, it won't expand the way you'd expect
Lloyd B.

Thanks for explanation. Maybe you could enlighten me: is [COLOR="Red"]cp[/COLOR] a built-in bash command or a separate program?
If it's built-in -- than I shouldn't be able to run any of built-in command with-out bash prefix.
If it's external program, than is it interprets the arguments by itself or asks the bash to get the file ... i'm confused.

And one more stupid question: isn't launching terminal - launching one of the shell interpretors (bash or sh...)?

Thanks.

Sasha.

---

### Post by sashaluda on 2009-12-03
> **lloyd_b said:**
> Not familiar with Gnome, but```
**Type: Application in terminal**
Name: Copy Flash
Command: cp /tmp/Flash* ~/Desktop/
Comment: Copy FLV files from TMP to Desktop
```with a type of "Application in terminal" you'd pretty much expect it to run a terminal.

Is there just a plain "Application" type?

(I run Xubuntu, which uses the Xfce desktop, so I can't test it for myself.  Under Xfce, there's a checkbox in the configuration to specify whether to run in a terminal or not).
Lloyd B.

That's right. But just "Application" option yields no result (not even an error message).

Ideally the goal is to run it as just an "Application", so that terminal window will not open. But I've reached my goal - no need for sh-file, and I run it from the drawer.

P.S. I still think there is another trick (how can it be otherwise - it's Linux after all) ;)

---

### Post by lloyd_b on 2009-12-03
> **sashaluda said:**
> Thanks for explanation. Maybe you could enlighten me: is [COLOR="Red"]cp[/COLOR] a built-in bash command or a separate program?
If it's built-in -- than I shouldn't be able to run any of built-in command with-out bash prefix.
If it's external program, than is it interprets the arguments by itself or asks the bash to get the file ... i'm confused.

And one more stupid question: isn't launching terminal - launching one of the shell interpretors (bash or sh...)?

Thanks.

Sasha.

First, a definition: A "shell" is a special program that acts as a "command interpreter" - it takes user input, maybe performs some processing on it, and then uses it to execute other programs (or functions built into the shell).

'cp' is an external program, not part of any shell.  

Your command is relying on "shell expansion" to provide some of the arguments to 'cp'.

What happens when you type "cp /tmp/Flash* /somewhere/else" in a terminal window is:

1.  The shell sees that "*", and expands it to the actual files.  Let's say it gets "/tmp/Flash1" and "/tmp/Flash2".

2.  The shell then executes the command "cp /tmp/Flash1 /tmp/Flash2 /somewhere/else".

Without the shell, the command "cp /tmp/Flash* /somewhere/else" will result in 'cp' trying to copy a file literally named "/tmp/Flash*", as it has NO inbuilt capacity for handling the wildcard.

The "terminal" (properly, it's a "terminal emulator" - a program designed to mimic the functionality of a physical terminal device) handles the job of taking input from the keyboard and passing it to the program, and taking output from the program and displaying it for the user.

You generally run a shell when you open a terminal window.  But there's no law that says you must.  For instance, you can run an interactive command-line program (such as "alsamixer") in a terminal window, with no shell required. 

"sh -c ..." is a special case of invoking the shell - it tells the shell to run the command that occurs after the "-c" switch, and then terminate.  In this way, you can use the command interpreter, but without it needing input from the keyboard.  Any output that the command generates will be displayed in the terminal window if there is one, or simply discarded if there is no terminal window.

So you can use shell commands without a terminal window, and a terminal window without a shell.  You *do* require a terminal window (or an actual terminal) to do interactive things with a shell.

I hope this clarifies things.  Or at least doesn't confuse you further :D

Lloyd B.

---

### Post by sashaluda on 2009-12-03
Amazing!
Thank you for correcting my "DOS"-thinking.

Turns out that MS's desire to write monolithic controll progam (one that includes system functions and built-in commands and printing function and ......) goes back to DOS times (command.com)! Later it developed into explorer.exe -- the thing responsible for all good or bad.

So, as far as I understand, terminal -- is the software responsible for communication between input and output (whatever it is - keyboard to printer/keyboard to monitor/mouse to monitor ...). It means more specialisation and separation of responsobilities between different pieces of software.

Thanks! Little bit of thinking ... and I've got what I wanted! No terminal window and job done from drawer! Here is the setup:

**Type:** Application
**Name:** Copy Flash
**Command:** sh -c "cp /tmp/Flash* ~/Desktop/"
**Comment:** Copy FLV files from TMP to Desktop

does the job well.

Thank you ALL. The problem is solved (knowledge and understanding is gained).

Sasha

---

