---
title: "KDE Menu launches bash scripts without environment variables"
date: 2012-03-23
forum: General Help
---

### Post by Iskendar on 2012-03-23
Hi all,

Trying to set up a little OpenCV demo for our open door at work, so I wanted to launch a bunch of scripts from the desktop. Tried adding them to the start menu, didn't work. Set 'Run in terminal' with the option --noclose, and then I saw that obviously some paths were missing. Apparently the shell starts without running .bashrc, so none of the environment variables are set (checked this). Clicking the script in dolphin or a folder view: same problem.
If I just start up a terminal and run the script from the command line, it works no problem. What am I missing here?

Running Kubuntu 11.10 with kde 4.7.

---

