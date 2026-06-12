---
title: "Problems with APT"
date: 2009-12-13
forum: General Help
---

### Post by nmaster on 2009-12-13
This happened to me a few times:
```
$ sudo apt-get install cups-pdf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups-pdf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up wallpaper-bamboo-zen-theme (1.2.6.jaunty.ppa1+nmu1) ...
cat: /usr/share/bisigi/bisigi: No such file or directory
/var/lib/dpkg/info/wallpaper-bamboo-zen-theme.postinst: line 11: /usr/share/bisigi/bisigi: No such file or directory
dpkg: error processing wallpaper-bamboo-zen-theme (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bamboo-zen-theme:
 bamboo-zen-theme depends on wallpaper-bamboo-zen-theme; however:
  Package wallpaper-bamboo-zen-theme is not configured yet.
dpkg: error processing bamboo-zen-theme (--configure):
 dependency problems - leaving unconfigured
Setting up wallpaper-ubuntu-sunrise-theme (2.1.4.jaunty.ppa1+nmu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          cat: /usr/share/bisigi/bisigi: No such file or directory
/var/lib/dpkg/info/wallpaper-ubuntu-sunrise-theme.postinst: line 11: /usr/share/bisigi/bisigi: No such file or directory
dpkg: error processing wallpaper-ubuntu-sunrise-theme (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-sunrise-theme:
 ubuntu-sunrise-theme depends on wallpaper-ubuntu-sunrise-theme; however:
  Package wallpaper-ubuntu-sunrise-theme is not configured yet.
dpkg: error processing ubuntu-sunrise-theme (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 wallpaper-bamboo-zen-theme
 bamboo-zen-theme
 wallpaper-ubuntu-sunrise-theme
 ubuntu-sunrise-theme
E: Sub-process /usr/bin/dpkg returned an error code (1)
neal@neal-laptop:/home/neal 
$ 

```

I tried removing the thing from my software sources but I get the same error.  Nothing is terribly wrong, but I hate seeing bugs.  What should I do?

---

### Post by llamabr on 2009-12-13
did you say you tried to remove bamboo-zen-theme?

---

### Post by nmaster on 2009-12-13
I think i removed it... I first commented out the lines I had added to /etc/apt/sources.list, but when that didn't change anything I doubted myself and went with the GUI.  I posted a screenshot of my 3rd part software sources.

how else would i remove the theme?

---

### Post by nmaster on 2009-12-13
i thought that these were popular themes so i'm surprised that i can't find other people with this problem

---

### Post by nmaster on 2009-12-13
well i couldn't fix it so i ended up just removing a bunch of things with dpkg and then autoremove.  i think i'll just stick with the default themes from now on, even if they aren't as sharp.

---

### Post by poliltimmy on 2009-12-13
This fixed mine. Add the file.. /usr/share/bisigi. Themes work fine now on my machine.

---

### Post by nmaster on 2009-12-13
thanks, but i guess now that i've changed my theme to one of the defaults i kind of like it!  changing things up is good though.  eventually i'll go back to one of those themes.  thanks.

---

### Post by Zorga on 2009-12-19
I have the same problem and I don't understand your solution. Could you please explain?

---

### Post by nmaster on 2009-12-20
i never tried it, but i think this is what should be done:

go to the terminal
```

sudo touch /usr/share/bisigi

```

if this doesn't work,  try opening the file in a text editor and adding a newline to the end.  i'm not really sure if this will work, but i hope it will.

---

