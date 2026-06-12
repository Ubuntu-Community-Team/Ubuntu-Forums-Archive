---
title: "Changing &quot;keypad delete&quot; from comma to period"
date: 2010-01-10
forum: General Help
---

### Post by waterwetter on 2010-01-10
Hello everyone,

I am using Ubuntu 9.10 in U.S. English with a German keyboard layout. Accordingly, pressing the delete button on the numeric keypad will produce a comma, which most applications do not recognize as a decimal. So I would like to ask for help in order to have the key produce a period.

I have tried editing the /usr/share/X11/xkb/symbols/de and changing the line
```
include "kpdl(comma)"
```in the "basic" section of the file to
```
include "kpdl(period)"
```which seemed like the perfect solution, but upon restarting an error message pops up and the keyboard layout is changed to U.S. English.

After some research, I found this suggestion:
```
cd /usr/share/X11/xkb/symbols
xkbcomp -lhlpR '*' -o ../symbols.dir
```which does nothing at all if used with sudo and produces an error message if used without.
Reverting changes to /usr/share/X11/xkb/symbols/de removes all errors.
Is there something else I need to do to have xkb accept my changes to the file?

Any help would be much appreciated.

Best regards,
Jake

EDIT: Sorry, it seems I was not being terribly smart here. It appears that
```
include "kpdl(comma)"
```does not *specify* a symbol to be mapped to the keypad delete key, but rather constitutes a command that integrates a pre-specified option into the layout file. Thus, simply *removing* the line works perfectly well, even without using the above suggestion to register the change to the file with xkb (or whatever it does).

Either way, thanks for reading. Unfortunately, I do not know how to close a thread in this forum.

---

### Post by rnerwein on 2010-01-10
try to use xmodmap (see man pages)
1. use: xev -  print contents of X events (keycode etc.)
2 run: xmodmap -pke > mymodmapfile.txt
3. edit the file mymodmapfile.txt to your behavior
4. run: xmodmap mymodmapfile.txt
hope this will help you
ciao

---

### Post by waterwetter on 2010-01-11
xmodmap works beautifully, thanks!

---

### Post by attila_66 on 2010-03-09
How to make a change like this permanantly??

My problem is: I have a comma on numeric keypad. But on for example calculator I have to use dot and want to change comma on that field as dot permanantly.

I already changed it temp with xmodmap.

---

### Post by waterwetter on 2010-03-10
I have found another approach that should help solve this problem:

Go to System -> Preferences -> Keyboard -> Layouts -> Layout Options... -> Numeric keypad delete key behaviour and switch to "Four-level key with dot".

Oddly enough, I have noticed some (probably unrelated) minor changes to **all** layouts, including that Right Alt + 8 will produce &#8226; instead of [ and Right Alt + + will produce ] instead of ~.

---

### Post by attila_66 on 2010-03-10
> **attila_66 said:**
> How to make a change like this permanantly??

My problem is: I have a comma on numeric keypad. But on for example calculator I have to use dot and want to change comma on that field as dot permanantly.

I already changed it temp with xmodmap.

Sorry foe convinience !!
I noticed today that changing the key is permanantly done.
Today my comma is still dot.
Thanks

---

### Post by isleshocky77 on 2011-01-12
I'm never going to remember this, so I figured I would post it here as well as to try and help anyone else who comes across this.

At some point the tip which I had given above stopped working. I don't know which update to Ubuntu did it, but that is neither here nor there. I once again was fed up and just ignored it until now.

New fix:

Reset all options to default values (uncheck everything).

Then check
 * Numeric keypad layout selection
 ** Legacy Wang 724
 * Numeric keypad delete behavior
 ** Four-level key with abstract separators

I had tried some other arrangements which worked for the numbers but messed up the period, and then that had those two but messed up the asterisk. Anyways, this now works.

---

### Post by tanec on 2011-09-13
I solved it permanently with one line in .bashrc file of the root and my own user

xmodmap mymodmapfile.txt, and they works fine :)

---

