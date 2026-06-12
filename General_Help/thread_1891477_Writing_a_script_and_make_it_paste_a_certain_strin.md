---
title: "Writing a script and make it paste a certain string of text"
date: 2011-12-05
forum: General Help
---

### Post by Dry Lips on 2011-12-05
I need a little help... I've got a certain code [a string of text] that is too long to remember in my head, and I wish to find a way to simply paste it whenever needed. I guess you'd write a script or something, and tie it to a shortcut.
 

 How would you do that? I need help with writing the script as well as linking it to a shortcut. :confused:

---

### Post by papibe on 2011-12-05
There are several options depending how sophisticated you want your solution.

Here's simple idea:
[LIST]
[*]Put your string in a file: /home/youruser/string.txt.
[*]Using 'Keyboard Shortcuts' set a new shorcut like Super+Z.
[*]Name it anything you want and the command would be 'gedit /home/youruser/string.txt'
[*]Any time you need the string you press Super+Z and the string file will be open on the editor.
[/LIST]
Does that help you?
Regards.

---

### Post by Dry Lips on 2011-12-05
**@papibe:** Thanks a lot for your suggestion, but I've already got the somewhat accessible. I've got the string in a sticky note, but I was trying to avoid opening a document, marking the text, hitting Ctrl-C, going back to my program, hitting Ctrl-V...

What you suggested would bring up the text, but I would still have to select the text, and copy it. I just want to be able to paste the string simply by hitting the shortcut...

But thanks for replying anyway :D

---

### Post by papibe on 2011-12-05
Which version of Ubuntu are you using?

I have an idea for little python script, but the code depends on your version.

Regards.

---

### Post by Dry Lips on 2011-12-05
> **papibe said:**
> Which version of Ubuntu are you using?

I have an idea for little python script, but the code depends on your version.

Regards.

11.04 at the moment... Should be Python 2.7.1+

---

### Post by papibe on 2011-12-05
I'm not able yet to test this in my 11.04 laptop, but this is working on my 10.04 desktop

```
#!/usr/bin/python

import pygtk
pygtk.require('2.0')

import gtk

# get the clipboard
clipboard = gtk.clipboard_get()

YourString = "This is a magic string."

# set the clipboard text data
clipboard.set_text( YourString )

# make our data available to other applications
clipboard.store()

```
What the script does it put a custom string (YourString) into the clipboard. So you would have to create a shortcut for this script (let's say Super+Z)

In order to get your string wherever you want, you would have to press Super+Z and then Ctrl-V.

Tell us how it goes.
Regards.

P.D.: I think with a little more work you can get all working with a single shorcut.

---

### Post by Dry Lips on 2011-12-05
**@papibe:** Thanks man! :popcorn:

This sure is a good beginning... Just a little übernoobish question... How would you name
the file you've created? I've never written scripts before :P Bash scripts are named
script.sh right?

---

### Post by papibe on 2011-12-05
The name is not that really important, but if you want to follow the common standard for a python script, then the name would end in .py

For example:
```
copypaste.py
```
Don't forget to add execution permissions to the file:
```
chmod a+x copypaste.py
```
Regards.

---

### Post by Dry Lips on 2011-12-05
Hey, hey! It works. My first successful python lesson! A KDE star for you
my friend: :KS Now I just need to find the python command for "paste 
contents of clipboard".

Cheers,
Dry Lips

---

### Post by papibe on 2011-12-05
I finally got into my 11.04 laptop. The script works here too.

I got something new for you. There's a library to automate X Windows events, so you can emulate the final paste (Ctrl+V).

Here's how I made it work:

Install the xautomation library:
```
sudo apt-get install xautomation
```

Set up a shortcut for Alt+V (Super+something doesn't seemed to agree with Unity). Set the following bash script as the commmad (superv.sh):
```
#!/bin/bash

/path/to/copypaste.py

sleep 1

xte 'keydown Control_L' 'key V' 'keyup Control_L'

```
The line 'sleep 1' is a pause. It does work without it, but you have to press and release super fast. With the pause works better.

Now when you press Alt+V the bash script will be called. The script calls the already working filling of the clipboard. Then there is a pause so that the actual shortcut does not conflict with the next event. Finally xte emulates a Control+V pasting your string wherever you need.

Test it and let us know how it goes.
Regards.

---

### Post by Dry Lips on 2011-12-06
> **papibe said:**
> I finally got into my 11.04 laptop. The script works here too.

I got something new for you. There's a library to automate X Windows events, so you can emulate the final paste (Ctrl+V).

Here's how I made it work:

Install the xautomation library:
```
sudo apt-get install xautomation
```Set up a shortcut for Alt+V (Super+something doesn't seemed to agree with Unity). Set the following bash script as the commmad (superv.sh):
```
#!/bin/bash

/path/to/copypaste.py

sleep 1

xte 'keydown Control_L' 'key V' 'keyup Control_L'

```The line 'sleep 1' is a pause. It does work without it, but you have to press and release super fast. With the pause works better.

Now when you press Alt+V the bash script will be called. The script calls the already working filling of the clipboard. Then there is a pause so that the actual shortcut does not conflict with the next event. Finally xte emulates a Control+V pasting your string wherever you need.

Test it and let us know how it goes.
Regards.

I tell you, it works like magic! :D Using the super key is no problem since I don't use Unity but classical Gnome2. Thanks a lot for your help, I would probably not have managed to solve this on my own, since I'm not into scripting/programming.

When I was 14 I did mess around a bit with Pascal, but this was before the internet became commonplace, so I got stuck and lost the interest... You know, perhaps I'll have to study a little Python now. ;)

Again, thanks a lot for your help!

---

