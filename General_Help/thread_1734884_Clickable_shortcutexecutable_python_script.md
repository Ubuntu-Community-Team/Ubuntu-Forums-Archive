---
title: "Clickable shortcut/executable python script?"
date: 2011-04-20
forum: General Help
---

### Post by James_Richards on 2011-04-20
I am fairly new to Linux, and in the last two days, I've learned a lot!  I am a LONG time heavy windows user since 1986, and have used Mac OS X at work for the last year.

I feel I am a more experienced user on the Windows platform; I have programmed a short game in BASIC and C++.  I have tons of games and one of my hopes is to get them working on Linux.

My problem; I have sucessfully downloaded a couple games, compiled their scipts and can play them by finding their executable and double clicking on them.  i have added them to my Games menu.  I downloaded a front-end for a game that is written in Python (Doomsday and Snowberry if you want to know) and have it running great!  However, I would like to create some kind of clickable link in my Games menu so that it'll start up Snowberry (snowberry.py) so I don't have to keep opening a terminal and 'cd' my way to it's folder and 'python file.py'.

Possible?  I keep searching on google and find nothing but references to creating executable files for Windows.:(

---

### Post by ttshivers on 2011-04-20
First thing you need to do is make the python file excecutable.  This article can help you with that: [http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/]("http://ma65p.wordpress.com/2008/08/04/how-to-make-a-file-executable-in-ubuntu/").  Next, you need to add it to the GNOME menu.  This article can help you with that: [http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html")

---

### Post by James_Richards on 2011-04-20
Yeah... ...  

I thank you for answering my questions, but I've followed those same instructions and it didn't work.

Anyone have anything else?

I thought I'd try changeing 'Type' from 'Application' to 'Application in Terminal'.  Still no go.

---

### Post by LemursDontExist on 2011-04-21
The key thing that seems to be missing from those instructions is that for your system to run a script, the script needs to tell it where the interpreter is.  Try putting

```
#!/usr/bin/env python
```

at the very start of your .py file, then do everything ttshivers recommended.  Unless your script already has that at the start.  In that case, I don't know what's wrong!

---

### Post by James_Richards on 2011-04-21
Yeah...  Still not working.

How about converting it into some kind of executable file for Linux?  possible?

---

### Post by James_Richards on 2011-04-21
Well, new development, so I'll see fi I can change the title of the post to match.

After I gave up on trying to make the shortcut in my Applications/Games menu for Python scripts...  I noticed that I can't seem to make ANY shortcuts.  All the ones placed by other programs and installs work...except mine...  I think I am missing something, but I have no clue at this point.

---

### Post by LemursDontExist on 2011-04-22
Well, to give you some basic background, for a script to run on a Linux system it needs to be

a) marked as executable and
b) include the shebang line at the top of the file so that the shell knows how to run it.

If you do both of these things to my_script.py, then in the folder containing the script you should be able to run the script from the command line by entering

```
./my_script.py
```

If that doesn't work, then the script isn't properly executable.

Furthermore, for a script to run under gnome without popping up a dialog asking what you want to do, you need to define a .desktop file (alternatively, create a launcher, which is the same thing).  The .desktop file tells the computer to run the script as a script instead of opening it in an editor.  It also tells the computer whether to run the script in a terminal or not.

I'm pretty sure that this is what ttshivers' menu tutorial walks you through, but you could try making a .desktop file manually.  Something like:

```

[Desktop Entry]
Name=My script name
Comment=A brief description
Exec=/path/to/my_script.py
TryExec=/path/to/my_script.py
StartupNotify=false
Terminal=false
Type=Application
```

ought to work.  Anyway, you haven't really given enough information to do more than offer a general overview.  I hope this helps!

---

