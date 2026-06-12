---
title: "Identifying application starter"
date: 2010-01-10
forum: General Help
---

### Post by JohnBUK on 2010-01-10
Sorry, this is a very basic question as I am a new but enthusiastic Ubuntu user.

When trying to install a Firefox add-on (and others) it asks for the "Application" to use ie if in Windows I would be looking for the "exe" file to paste into the preferences box. 

Where do I find the similar files in Ubuntu 9.10?

Thank you.

---

### Post by syrex314 on 2010-01-25
Which add-on are you trying to install?

This might not be related, but if you know the name of the application you need, you can usually locate it on the command line with 'which'. For example, if I want Firefox to use Evince to open a PDF, I can open a terminal and type "which evince"

syrex314@methuselah ~ $ which evince
/usr/bin/evince

The output shows evince is in /usr/bin

---

### Post by nullmind on 2010-01-25
Most executables are located in either /bin/ or /usr/bin/ ([http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html))

---

