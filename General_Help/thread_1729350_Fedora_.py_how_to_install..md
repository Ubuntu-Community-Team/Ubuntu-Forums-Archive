---
title: "Fedora .py how to install."
date: 2011-04-14
forum: General Help
---

### Post by warrior_juggalo on 2011-04-14
I cd to the directory, Run Python setup.py install.

[mitch@mitch ~]$ cd LostCountdown
[mitch@mitch LostCountdown]$ python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory
[mitch@mitch LostCountdown]$ ls
icon.png LostCountdownScreenlet.py Screenlet.package sounds themes
[mitch@mitch LostCountdown]$

What am i doing wrong?

---

### Post by ~Plue on 2011-04-14
> **warrior_juggalo said:**
> 
[mitch@mitch ~]$ cd LostCountdown
[mitch@mitch LostCountdown]$ python **setup.py** install
python: can't open file 'setup.py': [Errno 2] No such file or directory
[mitch@mitch LostCountdown]$ ls
**icon.png** **LostCountdownScreenlet.py** **Screenlet.package** **sounds** **themes**
[mitch@mitch LostCountdown]$

there isn't a setup.py in the directory....

anyway, if this is just a regular screenlet, all you need to do is copy the extracted folder to your ~/.screenlets directory (create one if you dont have) and it should be available from the screenlets manager

---

### Post by warrior_juggalo on 2011-04-15
Thanks, I'm at work at the moment but ill try it as soon as I walk in the door, do I drag the whole folder in or just Countdownscreenlet.py?

---

### Post by warrior_juggalo on 2011-04-15
Sorry, just read you post properly, whole folder, got it.

I'll let you know how I go in afew hours.

---

### Post by warrior_juggalo on 2011-04-15
Can't find screenlets manager, How do i get it?

---

### Post by ~Plue on 2011-04-15
> **warrior_juggalo said:**
> Can't find screenlets manager, How do i get it?
what you currently have is a screenlet  (atleast, thats what i can gather from the contents of the folder) it's kind of like plasma widgets in kde.
to use it, you need to first install the screenlets program from the software-center
once installed the screenlets manager would be available in system>preferences or applications>accessories

---

