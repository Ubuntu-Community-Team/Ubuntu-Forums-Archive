---
title: "How to run a terminal command without a terminal window popping out?"
date: 2010-01-30
forum: General Help
---

### Post by ophysis on 2010-01-30
Hi all,

I have created a launcher to run a terminal command. This command will run a mouse macro, but because the terminal window pops out, it gets in the way of the mouse.

Is there a way for me to run that command without the terminal popping out?


An example of one of the commands is:
```
cat macro1 | xmacroplay :0
```

Even better: Can I just run this command with a keyboard shortcut?

Tks

Andre

---

### Post by blur xc on 2010-01-30
> **ophysis said:**
> Hi all,

I have created a launcher to run a terminal command. This command will run a mouse macro, but because the terminal window pops out, it gets in the way of the mouse.

Is there a way for me to run that command without the terminal popping out?


An example of one of the commands is:
```
cat macro1 | xmacroplay :0
```Even better: Can I just run this command with a keyboard shortcut?

Tks

Andre

I'm not 100% sure of what you want, but alt-f2 brings up a run dialog.

Can you launch it form Nautilus?  And you can create a keyboard short cut for anything.  System-> Preferences-> Keyboard Shortcuts (in Gnome, anyway)...

BM

---

### Post by ophysis on 2010-01-30
Tried the Alt+F2 thing. Didn't work (I may have writen it wrong - not sure how to do it this way).
The command seems to need to run in the terminal.

I think I know how to create the shortcut, but I need to know how to run it (through the terminal - or not, maybe) without the terminal window popping out.

Tks

---

### Post by blur xc on 2010-01-30
> **ophysis said:**
> Tried the Alt+F2 thing. Didn't work (I may have writen it wrong - not sure how to do it this way).
The command seems to need to run in the terminal.

I think I know how to create the shortcut, but I need to know how to run it (through the terminal - or not, maybe) without the terminal window popping out.

Tks

Maybe someone else can chime in.  I don't understand what it means to run a program in the terminal w/o having the terminal window pop out.

To my mind- you either run a command in the terminal or not...

Sorry...

BM

---

### Post by ophysis on 2010-01-30
I see what you mean.

If you create a desktop luncher for a command in the terminal, the terminal will open while running the command and then shuts down.

And that's what I need NOT to happen. :) I just need the launcher to run without the terminal interfering.

Hope this clarified my intentions a bit. :)

Tks again.

---

### Post by pbrane on 2010-01-30
create a script.
```

#!/bin/bash
cat macro1 | xmacroplay :0
exit

```
Name the script, i.e., mouse_script.sh, then **chmod u+x mouse_script.sh** to make it executable. Place the script in the directory of your choice. I created a ~/bin directory because bash searches this if it exists.

Then add a keyboard shortcut in System->Preferences->Keyboard Shortcuts and bind it to a key combination like CTRL+F10 and then when you hit CTRL+F10 the script will execute without any terminal.

---

### Post by ophysis on 2010-01-31
> **pbrane said:**
> create a script.
```

#!/bin/bash
cat macro1 | xmacroplay :0
exit

```
Name the script, i.e., mouse_script.sh, then **chmod u+x mouse_script.sh** to make it executable. Place the script in the directory of your choice. I created a ~/bin directory because bash searches this if it exists.

Then add a keyboard shortcut in System->Preferences->Keyboard Shortcuts and bind it to a key combination like CTRL+F10 and then when you hit CTRL+F10 the script will execute without any terminal.

Hi pbrane,

I have been trying this, but when I press the keys I get an error:

Error while trying to run (1d1.sh)
which is linked to the key (<Shift><Control>F1)

When you create the keyboard shortcut, what exactly do we need to write in the command box?

Thank you for your help.

Andre

---

### Post by pbrane on 2010-01-31
> **ophysis said:**
> Hi pbrane,

I have been trying this, but when I press the keys I get an error:

Error while trying to run (1d1.sh)
which is linked to the key (<Shift><Control>F1)

When you create the keyboard shortcut, what exactly do we need to write in the command box?

Thank you for your help.

Andre

You should put the entire path to the script and any arguments that the script requires. In this case it looks like there are no arguments. I take it that when you run this from the command line it works? Try using complete paths to the commands you are running in the script too. 

What are the macros you are trying to run? Can you post the actual macros and commands?

Actually it may be possible to run the macros directly in the keyboard shortcut command field. Have you tried that?

---

### Post by pbrane on 2010-01-31
One more thing. It looks like xmacroplay requires a text string as input. i.e.,
```
echo "some X event(s)" | xmacroplay :0.0
```
Is that the kind of thing you are doing with "macro1"? I mean **cat** *should* work the same but maybe not.

An alternative to xmacro is xdotools. I've heard it's less buggy. But I have no experience using either. xdotoool would be used like **xdotool key F2** to send the F2 key to the X server.

---

### Post by ophysis on 2010-01-31
Ok, so:

Yes, it works from the command line (ALT+F2).
Yes, a launcher works as well.
No, the keyboard shortcut does not work (with the exact same command).

For all of them I'm writing:

/home/kitos/bin/1d1.sh

In this specific case the script contains (as you recommended):
```
#!/bin/bash
cat 1.d1 | xmacroplay :0
exit
```
1.d1 is the file with the macro (which contains xmacro commands and coordinates that makes the mouse click and move around)
xmacro is the program, of course.

Bare in mind that I'm not the most knowledgeable person when it comes to ubuntu, linux, etc.

There probably is a way of running the xmacro thing directly without the need of a script? I don't know, the info available about this program is minimal.

At least now the launchers work, which is great.

Thank you for that ;)

Andre

---

### Post by Iowan on 2010-01-31
Will it run in background - or does that just leave terminal window open?

---

### Post by ophysis on 2010-01-31
> **pbrane said:**
> One more thing. It looks like xmacroplay requires a text string as input. i.e.,
```
echo "some X event(s)" | xmacroplay :0.0
```
Is that the kind of thing you are doing with "macro1"? I mean **cat** *should* work the same but maybe not.

An alternative to xmacro is xdotools. I've heard it's less buggy. But I have no experience using either. xdotoool would be used like **xdotool key F2** to send the F2 key to the X server.

Now this is already too much for my knowledge. :)

I tried replacing cat with echo - doesn't work. I don't know what cat or echo are or do.

Tks

---

### Post by ophysis on 2010-01-31
> **Iowan said:**
> Will it run in background - or does that just leave terminal window open?

Now, with the script proposed by pbrane, it runs in the backgroud - no window popping up. :)

Just the keyboard shortcut no working now.

Ta

Andre

---

### Post by pbrane on 2010-01-31
if **1.d1** is a text file then you should use **cat**. echo would want a quoted string as input.

So the script works, but not the keyboard shortcut? 

Make sure you use a complete path in the script, like 
```
 cat /home/user/bin/1.d1 | xmacroplay :0.0 
```

---

### Post by ophysis on 2010-02-01
It's really weird. It work's everywhere, except on the keyboard shortcut thing.

Don't really understand why.

Tks anyway.

Andre

---

