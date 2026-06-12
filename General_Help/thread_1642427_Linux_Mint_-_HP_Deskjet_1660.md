---
title: "Linux Mint - HP Deskjet 1660"
date: 2010-12-10
forum: General Help
---

### Post by GermanGuaimare on 2010-12-10
Hey guys. I'm having a problem with my printer. I just installed Linux Mint LXDE, and i liking it. But the issue came when I installed my printer and tried to print a test page, my printer does nothing. The printer manager on my system says that the job is completed, but nothing happens, i can't print anything. If someone knows the solution, please comment. Thanks in advance.

---

### Post by kanishkdudeja on 2010-12-10
have you installed hplip ?

if not..

```
sudo apt-get install hplip
```

---

### Post by Spyderkid on 2010-12-10
try running this:

```

sudo apt-get install hplip

```

---

### Post by GermanGuaimare on 2010-12-10
Guys, I did what you said but still I can't print. What should I do next?

---

### Post by kanishkdudeja on 2010-12-11
umm try solution in post 3 of this thread..

[http://ubuntuforums.org/showthread.php?t=1467179](http://ubuntuforums.org/showthread.php?t=1467179)

---

### Post by GermanGuaimare on 2010-12-11
Guys, I'm trying with the automatic installer, but it says I need some dependencies, could you tell me what dependencies do I need? This is what the terminal says:

```
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

```Sorry for all the trouble and thanks for your help.

---

### Post by kanishkdudeja on 2010-12-11
this screenshot is showing only 1 missing required dependency - gcc..where are the other 6 ?

btw u cn install gcc by:

```
sudo apt-get install gcc
```

---

### Post by GermanGuaimare on 2010-12-11
> **kanishkdudeja said:**
> this screenshot is showing only 1 missing required dependency - gcc..where are the other 6 ?

btw u cn install gcc by:

```
sudo apt-get install gcc
```

Don't know what are the other dependencies, and ggc seems like it was already installed.

---

### Post by kanishkdudeja on 2010-12-11
umm..check hplip or hpijs log whichever u hav installed..mayb u will find the required dependencies there..n ur internet connection shud b active during install..if ur internet connection was not active during the install mayb thats why it could not install the required dependencies.

---

