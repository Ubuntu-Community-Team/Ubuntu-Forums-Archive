---
title: "Bug in Printer manager"
date: 2010-01-17
forum: General Help
---

### Post by Frido Raida on 2010-01-17
summary: After a wrong operation done into the printer manager (menu system/administration/printing) the printer manager doesn't work anymore.

description: I tried to add a network printer and i make a mistake in the address specification of network printer
after this wrong operation when i press on "system/administration/printing" menu command, the hourglass started, pass a little bit of time and then disappear without open any program and/or window
the other programs relate to printer work fine ("application/accessories/manage print jos", "System/Preferences/Default printer")

is there a way to solve this problem?
do i have to re-install the printer manager? 
which is the way to re-install the graphic printer manager?

some information about my system:
OS: Ubuntu 9.10 (upgrade by update manager at January 17 2010
graphic shell: Gnome desktop 2.28.1

many thanks and friendly regards

---

### Post by cogier on 2010-01-17
I am not sure why you can't get into Print Manager but you may be able to change the printer settings in CUPS. Follow this link [http://localhost:631/printers/]("http://localhost:631/printers/")

Hope that helps.

---

### Post by Frido Raida on 2010-01-19
[]("http://ubuntuforums.org/member.php?u=691609")the printer manager (by browser) works fine
I'm able to manage all printers
the "system/administration/printing" is still bad
thank you for the answer

> **cogier said:**
> I am not sure why you can't get into Print Manager but you may be able to change the printer settings in CUPS. Follow this link [http://localhost:631/printers/](http://localhost:631/printers/)

Hope that helps.

---

### Post by plucky on 2010-01-19
> **Frido Raida said:**
> []("http://ubuntuforums.org/member.php?u=691609")the printer manager (by browser) works fine
I'm able to manage all printers
the "system/administration/printing" is still bad
thank you for the answer

From a terminal ```
system-config-printer
``` and see if there are any error messages.

Good Luck

---

### Post by Frido Raida on 2010-01-19
i've executes the command  "system-config-printer" by 'sudo'
the result is:
[I]Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 108, in <module>
    from GroupsPane import *
  File "/usr/share/system-config-printer/GroupsPane.py", line 21, in <module>
    from GroupsPaneModel import *
  File "/usr/share/system-config-printer/GroupsPaneModel.py", line 19, in <module>
    import libxml2
  File "/usr/lib/pymodules/python2.6/libxml2.py", line 1, in <module>
    import libxml2mod
ImportError: /usr/lib/pymodules/python2.6/libxml2mod.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference[/I]

it seems that something going wrong but i don't know what

thanks for the help

---

### Post by plucky on 2010-01-19
> Traceback (most recent call last):
File "/usr/share/system-config-printer/system-config-printer.py", line 108, in <module>
from GroupsPane import *
File "/usr/share/system-config-printer/GroupsPane.py", line 21, in <module>
from GroupsPaneModel import *
File "/usr/share/system-config-printer/GroupsPaneModel.py", line 19, in <module>
import libxml2
File "/usr/lib/pymodules/python2.6/libxml2.py", line 1, in <module>
import libxml2mod
ImportError: /usr/lib/pymodules/python2.6/libxml2mod.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference


Checkout this answer on [Launchpad](https://answers.launchpad.net/ubuntu/+source/libxml2/+question/90804)


Good Luck

---

