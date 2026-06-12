---
title: "Matlab shell script file location and linking problem!!"
date: 2010-12-09
forum: General Help
---

### Post by rcasiano on 2010-12-09
Hello, I'm having a problem starting Matlab from the terminal. I would like it to start simply by typing 'matlab' into the terminal window (where it reads 'rene@ubuntu:~$') at the beginning. I suspect it's because the file to run Matlab is not in the usr bin. It is instead in '/usr/local/MATLAB/R2010b/bin'. If I open up a window and go to that folder and open the matlab shell script with the 'open in terminal' option, Matlab runs fine. I think I need to link the bin or file...or both, that the Matlab file is in to the usr/bin to solve my problem. But...I don't know how. Can anybody please show me the syntax, but more importantly explain the reasoning behind it? I would like to learn to become more proficient at Linux. Thank you for your time!

---

### Post by Bazirker on 2010-12-10
I also have this problem.  Glad to see I'm not the only one, I was starting to feel like a dunce!

---

### Post by rcasiano on 2010-12-11
Bump

---

### Post by rcasiano on 2010-12-11
If anybody is having this problem, check this out:

[http://ubuntuforums.org/archive/index.php/t-1386221.html](http://ubuntuforums.org/archive/index.php/t-1386221.html)

Follow SlugSlug's instructions.

---

### Post by Bazirker on 2010-12-22
There's another shorter way to accomplish this, although via a less elegant solution.  I didn't want to run MATLAB from the command line but instead just wanted a menu button to click, so I did this:

1.)  Follow the instructions here to get a launcher icon:  [https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB")

2.) Edit the menu button via System -> Preferences -> Main Menu, then find the MATLAB button under "Programming"

3.) Change it so that instead of it running 'matlab -desktop', it instead contains the path to the launcher script, e.g. '/usr/local/MATLAB/R2010b/bin/matlab -desktop'

Again, this is less elegant than if you were to follow SlugSlug's instructions (which I couldn't get to work, although that might be related to the empty Guinness glass next to my keyboard), but if all you want is a menu button, it saves you a bit of time and is more GUI-based.

---

