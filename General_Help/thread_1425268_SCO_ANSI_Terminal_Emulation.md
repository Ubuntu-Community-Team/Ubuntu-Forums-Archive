---
title: "SCO ANSI Terminal Emulation"
date: 2010-03-08
forum: General Help
---

### Post by flyeng4 on 2010-03-08
I running 9.10 as a workstation.  On a RHEL server at work we have an inventory system that requires a ssh session to run the program.  One of the problems that I am running into is that the program requires ANSI F6.  I believe that this could be solved if I could find a decent Terminal Emulator that supported SCO ANSI.  Do you know of any?

Another solution would be to send an escape sequence to the terminal?  Does anyone know the escape sequence for ANSI F6?  If so, how do I bind this to a keyboard short cut?  

Another more general question is, how do I create a keyboard shortcut where I can hit something like "Shift-Ctrl-T" and "Hello World" will show up in the terminal.  I have ran into a couple instances where doing something like this might be helpful.

---

### Post by dcstar on 2010-03-08
> **flyeng4 said:**
> I running 9.10 as a workstation.  On a RHEL server at work we have an inventory system that requires a ssh session to run the program.  One of the problems that I am running into is that the program requires ANSI F6.  I believe that this could be solved if I could find a decent Terminal Emulator that supported SCO ANSI.  Do you know of any?


Attached is a Windows SCO terminal emulator (from SCO itself, many years ago).

You can install it on a Windows PC and capture the keys to work out what you need.

---

### Post by flyeng4 on 2010-03-09
I will give it a try.  Actually, I have a SCO ANSI terminal emulator for windows that the others in the office use.  The problem is, is that I run Ubuntu. Is there any way to emulate SCO ANSI in Linux?

---

### Post by DaleEMoore on 2011-01-05
This is a really good question flyeng4! I've wondered the same thing several times. Have you found a solution to your problem? (Care to share?)

---

### Post by flyeng4 on 2011-01-05
I ended up using a script that modifies xterm. Worked well.

```

#!/bin/bash
xterm -title "SPECIAL SESSION" -bg black -fg white -xrm \
        "XTerm*VT100.Translations:       #override\n\
        <Key> BackSpace: string(0x08)\n\
	<Key> F1:         string(0x1b) string("[M") \n\
	<Key> F2:         string(0x1b) string("[N") \n\
	<Key> F3:         string(0x1b) string("[O") \n\
	<Key> F4:         string(0x1b) string("[4") \n\
	<Key> F5:         string(0x1b) string("[Q") \n\
	<Key> F6:         string(0x1b) string("[R") \n\
	<Key> F7:         string(0x1b) string("[7") \n\
	<Key> F8:         string(0x1b) string("[8") \n\
	<Key> F9:         string(0x1b) string("[U") \n\
	<Key> F10:         string(0x1b) string("[V") \n\
	<Key> F12:         string(0x1b) string("[X") \n\
	<Key> F11:         string(0x1b) string("[W") "\
        -font -*-*-*-*-*-*-20-*-*-*-*-*-*-* -e ssh user@123.456.789.012

```

-Bill

---

### Post by tranbo2@yahoo.com on 2011-01-29
Bill, thanks for the script.  How do I install the script?

---

### Post by TheHackOps on 2011-01-29
tranbo2, if you mean run it then copy it and make a new file called script.sh make it executable and run it in a terminal

EG: ./script.sh

---

### Post by lsutiger on 2013-04-01
> **TheHackOps said:**
> tranbo2, if you mean run it then copy it and make a new file called script.sh make it executable and run it in a terminal

EG: ./script.sh

OK, I almost got this running, but not 100%. I have a server I log into using scoansi-old. How can I modify this script to reflect the correct commands for the function keys? Is there a way to capture what the function keys are currently doing from my current program?
I currently use smatrterm in windows, but would LOVE to have it work linux --> linux.

---

### Post by Toz on 2013-04-01
Please do not post to threads that are older than one year in age. Instead, create a new thread and reference this one. Alot may have changed since the last time anyone posted here.

Thread closed.

---

