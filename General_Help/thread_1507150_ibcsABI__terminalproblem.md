---
title: "ibcs/ABI  terminalproblem"
date: 2010-06-11
forum: General Help
---

### Post by philippjosefrichard on 2010-06-11
I am using ubuntu 10.4

In order to run my old XENIX-application based on INFORMIX I sucessfully compiled and loaded the needed modules with ibcs3.

so I can start my ancient application without an ERROR. I suppose that the compilation was ok, because I can see the normal messages of my application and I can input the wanted letters. The reaction of the application is normal. BUT there is a mismatch of lines in the terminal-emulation xterm or terminal.

In "Bildschirmfoto2" you can see how the correct display should be.
In "Bildschirmfoto3" you can see the mismatch of lines.

When I start the INFORMIX menu for the database with isql you can see in "Bildschirmfoto4" the unprintable signes instead of INFORMIX-menu.

Question: Is this mismatch due to an error in the terminal emulation or in the Kernel-modules compiled by ibcs3?

Has this problem something to do with termcap/terminfo?
Where should I  look for information to solve this problem?

Thanks for hints to solve that problem
Philipp

---

### Post by ibuclaw on 2010-06-11
Do you know how to use gdb / cgdb ?

First step I'd do is recompile with debug flags and no optimising. Assuming this is C your application is coded in, the flags are:
```
-g -O0
```

Then you can make a breakpoint in the application, and step through it until the unprintable signs show up. So at least then you know where it happens, and what function.

By the way, is this an app that uses the curses library?

---

### Post by itcotbtoemik on 2010-06-11
The likely problem is that the terminal is setup to expect
UTF-8 encoding, and that the application is writing ISO-8859-1
(or similar) 8-bit encoding.  The character codes between
128 and 255 have different meaning, and you'll see odd
characters displayed.

The way to work around this is to ensure that the terminal
expects the 8-bit encoding.  (With xterm, there's a menu
entry that controls this, though some additional tweaks
may be needed; other terminal emulators require a bigger
hammer).

---

### Post by philippjosefrichard on 2010-06-14
Thanks for reply.
The Line-problem begins when a DISPLAY FORM is used.
So I suppose, itcotbtoemik's answer could be the way of solvage.
In this direction I had tried around, but could not find the correct adjustment.

Does my app use ncurses? How can I know that? 
This app is compiled with a INFORMIX-version from 1989 !
ncurses is devellopt for Linux. In these days Linux was laying in the pampers, I suppose. Therefor I suppose NO.

This App was running on XENIX.
Lateron it was running in Redhat Linux and Fedora Core until FC3.
At present I am working with Fedora Core 3. On higher Fedora Core it does not work. Nor does it in Ubuntu.

I have got a termcap-file. With this information I probaply could understand which adjustment would be necessary. But I do noct understand termcap.

The section for vt100 in the termcap-File:


> 
# vt100 - really vt102 without insert line, insert char etc.
vt|vt100|DEC vt100 compatible:\
    :im@:mi@:al@:dl@:ic@:dc@:AL@:DL@:IC@:DC@:\
    :tc=vt102:



Which adjustment will be necessary?

thanks for help
Philipp

---

### Post by itcotbtoemik on 2010-06-14
My understanding is that the ibcs3 stuff provides
its own curses library and uses only termcap.  (It's
been a while since anyone commented on ibcs3, so I'm
working from recollections).  You should be able to
see what the application uses by doing a "strings" on
the executable.  Common things to look for are

a) TERMCAP (used as an environment variable)
b) TERMINFO (used as an environment)
c) pathnames containing "termcap" or "terminfo".
d) possibly other strings containing "term" or "TERM".

In the termcap entry, keys are given as strings.
I'd check on "kb" and "KD", and would expect to
see something like

    :kb=^?:
or
    :kb=^\177:

rather than

    :kb=^H:

for Linux.

---

### Post by philippjosefrichard on 2010-06-14
Sorry, but I do not understand what that means:
> **itcotbtoemik said:**
> 
You should be able to
see what the application uses by doing a "strings" on
the executable. 



At present I am on the Computer where the applicateion works (FC3). 
I could do now changes in the Code of my the application to do something, what shows me in the one Computer (FC3) and the other "Ubuntu 10.4) which executables are in use?

But as I do not understand the termcap-stuff I do not know what string should be done.

I made an observation: In the PC with FC3, where the old app do work, I entered TERM=ANSI and could see the same unprintable signs like you could see in "Bildschirmfoto4". But when I enter TERM=linux or TERM=vt100 then the INFORMIX-menu is visible and do work. BUT the same procedur did not change anythin at UBUNTU. 
I suppose, this is due to the fact,  that ubuntu do not use termcap ???
Is it?
Philipp

---

### Post by itcotbtoemik on 2010-06-17
There are several points.

a) I pointed out that there may be a problem if the terminal
emulator is using UTF-8.  That's partly determined by your
locale settings and the terminal (it's unclear which terminal
emulator you're using).

b) your application probably isn't using ncurses, but the
place where it gets its data can be inferred by looking at
strings extracted from the binary.

c) the pictures don't seem to be showing line-drawing,
though you mention that in comparing the ansi versus linux
or vt100.  The latter two have line-drawing, but it's usually
implemented incompatibly between the two.

d) yes, Ubuntu doesn't use termcap (and may not supply it).
Its locale support is basically UTF-8 encoding and ASCII.
There's apparently no support for ISO-8859-x encodings as
your application may expect.

---

### Post by philippjosefrichard on 2010-07-29
May be this helps to find the solution:

When I start the old aplication which is written in 4gl, compiled with informix with a C-compiler (i suppose), the "DISPLAY FORM" command from the aplication cannot display the form correct.
But the menu bar is displayd correct. 
the prompts are displayed correct in the prompt-line of the form.
the Prompt does accept the expected letters and does react correct. 
For example: 
the prompt-Code in the aplication 
'PROMPT "Please enter a or b:" FOR p_answer'  
'IF p_answer = "a" THEN CALL nextProgram()  END IF ' 
shows 
"Please enter a or b:" and waits for the answer

When I enter "a", then the letter "a" is displayed. But then nothing happens.
Only when I press contorl-C the aplication goes on with the 
nextProgram()

This control-C is necessary to go on. 

Control-R does show the form correct !!
normally control-R does rewrite the screen correctly if there is a wrong display.
but here control-R does only show the correct form, but the problem is not solved.

What does that mean?

Control-C does a break normally. 
Why is this control-C necessary to go on with the program?

So I suppose:
The problem is the lac of ability to display the signs on the screen correctly while the binaries of the application do work properly.

Am I right?

I am trying with putty. puTTY can be tuned with ISO-8859-1
There are possibilites of 
Set Various terminal options:
Auto wrap mode initially on
DEC Origin Mode initially on
Implicit CR in every LF
Implicit LF in every CR
...
But I cannot try out a solution.

Could I find the Solution in the /home/user/.profile of the old XENIX-Computer?
TERM=ANSI
this was displayed on the old Terminals

thanks for hints

Philipp

---

