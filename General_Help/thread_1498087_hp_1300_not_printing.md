---
title: "hp 1300 not printing"
date: 2010-05-31
forum: General Help
---

### Post by drolasca on 2010-05-31
Hello, 

I installed an hp 1300 AIO printer on Ubuntu 8.10.  The printer copies fine, so I know that it has ink.  However, whenever I print the printer will look like it is printing but will not actually put any ink on the page.  Is there anything I can do to fix this? 

I ran sudo hp-check -r and these errors came up---

Checking PyQt version...
error: NOT FOUND OR FAILED TO LOAD!

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)

Thank you

---

### Post by cogier on 2010-05-31
Have you installed HPLIP?

---

### Post by drolasca on 2010-05-31
I don't think so, I am pretty new to this and just let the computer take control.  Can I get this from the terminal or through the synaptic manager or do I have to go to the hp website?

Thanks

---

### Post by cogier on 2010-05-31
It should be available in the Repository. It has been some time since I touched 8.10 so I am not sure but on the Application Menu is there an "Add software" option? You should find it there or in Terminal run ```
sudo apt-get install hplip
```.

Hope that helps.

---

### Post by drolasca on 2010-05-31
I ran that command and got hplip, but I am still coming up with these 5 errors:

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
error: NOT FOUND OR FAILED TO LOAD!

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: python-ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: python-dbus - Python bindings for dbus...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.

---

### Post by cogier on 2010-05-31
Looking at the output you are missing some Python add-ons. I have had a look to see how mine is set up but there are a lot of Python add-ons selected and as I am running 10.04 I don't want to give you instructions that might break things.

You might be better off if you upgraded your software as I have not had a problem installing HPLIP on 9.04, 9.10 or 10.04.

---

