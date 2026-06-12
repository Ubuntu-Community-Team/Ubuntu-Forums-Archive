---
title: "How do I change the icon in the launcher?"
date: 2012-04-18
forum: General Help
---

### Post by Ifaistos on 2012-04-18
Hello everyone :)

I have downloaded and installed a python program, manually.
It is a python script which I have allowed to run as an application.
Because it was not installed automatically I can't find it using the dash.

So I searched for it, and when it was run, I chose to "keep it in launcher".

The problem is that the icon I see is the one python.
There is a .png icon for the program in the folder, but I have no idea how to associate the .png icon with the program and how to change the icon in the launcher with the icon in the program folder.

Anyone?

Thanks for your help in advance :-)

---

### Post by Ifaistos on 2012-04-18
bump :-)

---

### Post by wojox on 2012-04-18
Look in /usr/share/applications and see if there is a .desktop file for your app and edit it to the correct icon.

---

### Post by Ifaistos on 2012-04-19
Thank you for your suggestion :)

I looked at each and every one of the .desktop files but there was not one for my app.  There was one for python, but not for pyfa (which is the app I am looking for).

Any other ideas, please?

---

### Post by hakermania on 2012-04-19
Ok. The solution is pretty simple. Follow these simple steps:
1) Place your python script and icon inside a "stable" directory (e.g. not in your desktop, because in the future you may accidentally move it, delete it etc, for example, Documents/ would be a nice place for a script to be)
2) Open Gedit using 'gksudo gedit' from inside a terminal. You will be asked for your login password and Gedit will open.
3) Insert these inside Gedit:
```

[Desktop Entry]
Version=1.5
Name=Pythonitic
Comment=Do something
Exec=/home/user/Documents/python.py
Icon=/path/to/icon
Terminal=false
Type=Application
Categories=Utility;Application;

```and edit everything after all the '='
Most important fields are 'Name' (you will use it to find your application through Dash later), 'Exec' (it should be the path to your python script), and 'Icon', which is what really matters to you right now (it should be the path to the png icon of your application).
4) After finishing Editing, save the file to /usr/share/applications/programname.desktop (where programname place anything you like, preferably similar to your program's real name)
5) You are done, now you will be able to find your application through Dash! Remember **not **to move the icon or the python script after this operation (remember step **1**), or the .desktop file will not be able to find them and thus the script will not be able to execute through Dash, after moving them to other directory.

---

### Post by Ifaistos on 2012-04-19
Hello :)
Excellent answer... I am sure we are on the right track.
This is what I did :

[Desktop Entry]
Version=1.5
Name=Pyfa
Comment=EVE Python Fitting Assistant
Exec=/home/pyfa/pyfa.py
Icon=/home/pyfa/icons/pyfa.png
Terminal=false
Type=Application
Categories=Application;

I removed utilities from categories because it was becoming red in gedit.  (no idea why).
I also didn't move the pyfa.png.  I left it where it was and I changed the directory in the path for the .png.

I don't think that it makes a difference.

Anyway... now I can find pyfa from the dash, but I can't run it.
Maybe it has to do with exec line... did I do smt wrong?
Maybe I need to put another exec line, that will include python and then the pyfa.py script?

Thanks a lot for the help :-)

[edit]

I copied the icon to /home/pyfa and changed the corresponding line.
It didn't make any difference as expected.  
I still can't run it... and still see the pyfa icon as a sheet of paper, instead of the .png icon, in dash, under applications.

---

### Post by Ifaistos on 2012-04-19
I fixed it!

Thank you for your suggestion... it worked like a charm.
The error was totally mine.

I had added the wrong path...

instead of /home/evans/pyfa I had used /home/pyfa directory.

Once I fixed that, it worked great!
Thank you so much for your suggestion...

Marking this as solved.

---

### Post by hakermania on 2012-04-19
Hey, nice :)
Sorry for the relatively late response but I couldn't have checked earlier :)

---

