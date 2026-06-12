---
title: "Software center broken"
date: 2010-12-29
forum: General Help
---

### Post by Trogladyte on 2010-12-29
It used to work, but now it starts loading but window does not open. 

From a terminal I get:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from softwarecenter.view.widgets.mkit import floats_from_string
  File "/usr/share/software-center/softwarecenter/view/widgets/mkit.py", line 29, in <module>
    from mkit_themes import Color, ColorArray, ThemeRegistry
EOFError: EOF read where object expected
trog@trog-EasyNote-MZ36:~$  			 		

I tried reloading it via synaptic - seems t stall fr ages when processing h-colour theme triggers.

Any thoughts as to how to resolve?

---

### Post by sikander3786 on 2010-12-29
From Terminal, try these commands and post the output as well.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by Trogladyte on 2010-12-29
> **sikander3786 said:**
> From Terminal, try these commands and post the output as well.

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```

Thanks.

This is the output from the first
trog@trog-EasyNote-MZ36:~$ Traceback (most recent call last):
bash: syntax error near unexpected token `most'
trog@trog-EasyNote-MZ36:~$ File "/usr/bin/software-center", line 88, in <module>bash: syntax error near unexpected token `newline'
trog@trog-EasyNote-MZ36:~$ from softwarecenter.app import SoftwareCenterApp
from: can't read /var/mail/softwarecenter.app
trog@trog-EasyNote-MZ36:~$ File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
bash: syntax error near unexpected token `newline'
trog@trog-EasyNote-MZ36:~$ from softwarecenter.view.widgets.mkit import floats_from_string
from: can't read /var/mail/softwarecenter.view.widgets.mkit
trog@trog-EasyNote-MZ36:~$ File "/usr/share/software-center/softwarecenter/view/widgets/mkit.py", line 29, in <module>
bash: syntax error near unexpected token `newline'
trog@trog-EasyNote-MZ36:~$ from mkit_themes import Color, ColorArray, ThemeRegistry
from: can't read /var/mail/mkit_themes
trog@trog-EasyNote-MZ36:~$ EOFError: EOF read where object expected
EOFError:: command not found
trog@trog-EasyNote-MZ36:~$ trog@trog-EasyNote-MZ36:~$ 


the second code is returning "command not found". Hang on, I'll try again.

---

### Post by Trogladyte on 2010-12-29
> **sikander3786 said:**
> From Terminal, try these commands and post the output as well.

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```


OK the second code asked for a password, and when I entered it, returned to the prompt.

---

### Post by Trogladyte on 2010-12-30
Just tried that again, and got a different result:

trog@trog-EasyNote-MZ36:~$ sudo apt-get install -f
[sudo] password for trog: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqt4-sql-mysql libqt4-dbus linux-headers-2.6.35-22
  mysql-common linux-headers-2.6.35-22-generic libqtcore4 stellarium-data
  libqt4-sql libqt4-xml libqt4-network libmysqlclient16 libqtgui4
  libqt4-script libaudio2 libmng1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Trogladyte on 2011-01-01
Bump

---

