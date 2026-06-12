---
title: "gsettings missing"
date: 2012-01-04
forum: General Help
---

### Post by jeeves on 2012-01-04
I should be able to run gsettings, but every time I run a "gsettings" command in a terminal I get the message "**command not found: gsettings**"

Mind you, I  did not do the typical Ubuntu install on this computer. I did an command line install with the alternate CD, then manually added in lightdm & gnome-shell (the idea was to make a purely gnome-shell version of oneiric). Everything has worked great except for this one issue.

I also checked that I have the following installed:
[B]gsettings-desktop-schemas
dconf-gsettings-backend
dconf-tools
libdconf0
 [/B]

---

### Post by jeeves on 2012-01-04
I ran a gsettings command using the /bin/bash shell instead of my usual /bin/zsh. The Bash shell gave me the hint I needed to solve this:
"The program 'gsettings' is currently not installed.  You can install it by typing: sudo apt-get install libglib2.0-bin

So I installed **libglib2.0-bin** and that solved the problem.

---

### Post by shimmey on 2012-01-29
Great pity!

I met the same problem, but the above method doesn't work on my laptop. The bash show me:
E: Couldn't find package libglib2.0-bin
Now my system is ubuntu 10.04.3 LTS

Anyone could give me some more information? Thanks for all!

---

