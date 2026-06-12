---
title: "Python Help"
date: 2011-10-03
forum: General Help
---

### Post by cddpys on 2011-10-03
Hey i need some help running python.  I used kate to write a .py file but how to i compile/run that file now?

thanks

---

### Post by Pynalysis on 2011-10-04
> **cddpys said:**
> Hey i need some help running python.  I used kate to write a .py file but how to i compile/run that file now?

thanks

Python module = .py

Here are two methods to run your Python module

Method one
Open a terminal window and cd to the directory with the .py

Example - Python module (.py file) is on the Desktop
From a terminal window:

cd /Desktop
python name.py

Method two
Example - Python module (.py file) is on the Desktop

At the top of the Python module include this for the first line:

#!/usr/bin/env python

From a terminal window:
cd /Desktop
chmod +x name.py
./name.py

~Pynalysis

---

