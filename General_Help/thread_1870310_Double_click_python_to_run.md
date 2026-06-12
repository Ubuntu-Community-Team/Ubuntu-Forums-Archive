---
title: "Double click python to run"
date: 2011-10-27
forum: General Help
---

### Post by olligobber on 2011-10-27
Is it possible to make anything a user could double click to run a python command, without opening terminal, navigating to the file, and typing in "python2.7 file.pyc" or making a menu shortcut. Just a shell script would do, but they don't seem to run with a double click.

---

### Post by Pynalysis on 2011-11-03
> **olligobber said:**
> Is it possible to make anything a user could double click to run a python command, without opening terminal, navigating to the file, and typing in "python2.7 file.pyc" or making a menu shortcut. Just a shell script would do, but they don't seem to run with a double click.

Steps to do this
Example will be to create an executable Python module on your Desktop

1) Create a python module with .py extension
    open a terminal
    gedit file.py

2) Add the shebang line as the first line in the Python module- this says use Python
    #!/usr/bin/env python

3) Add Python code you want to execute
    print "Works..."
    raw_input('Press enter to close...')

4) Save file to Desktop
5) Run this to from a terminal to make the program executable
    cd Desktop
    chmod +x file.py

6) Double click on the file and select run in terminal

---

### Post by olligobber on 2012-01-01
> **Pynalysis said:**
> Steps to do this
Example will be to create an executable Python module on your Desktop

1) Create a python module with .py extension
    open a terminal
    gedit file.py

2) Add the shebang line as the first line in the Python module- this says use Python
    #!/usr/bin/env python

3) Add Python code you want to execute
    print "Works..."
    raw_input('Press enter to close...')

4) Save file to Desktop
5) Run this to from a terminal to make the program executable
    cd Desktop
    chmod +x file.py

6) Double click on the file and select run in terminal

It is steps 2 and 6 that are the most help.

However, does running a .pyc file change anything?

NOTE: I have not tried this solution. I will in the near-ish future.

EDIT: Forgot to say thankyou :D

---

