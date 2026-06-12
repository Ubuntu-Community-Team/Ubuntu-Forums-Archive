---
title: "gnome-terminal dying/disappearing with custom launch arguments"
date: 2011-01-24
forum: General Help
---

### Post by earthmeLon on 2011-01-24
I work on a number of servers and do so many repetitive tasks that it's easier for me to make launchers on my desktop for these tasks.  It's also necessary for opening windows in my secondary screen.

I like to view the error logs as I work, so I have a screen session on my servers that 'tail -f /the/error.log' for easy viewing.

I set up a launcher on my desktop that launches the following command:
```
gnome-terminal --display :0.1 --geometry=156x33 -x ssh -t my-server 'screen -r'
```

The command works perfectly.  The window is created on the correct screen, with the correct size and information.  The problem is **gnome-terminal will exit/crash with no errors after a little while.**  This happens sometimes when I get up from my computer as well as while I am working on it.

I am saying that there are no errors because I have opened a terminal and ran the command in that terminal.  When the new gnome-terminal closes, there are no errors or abnormal output on the generating gnome-terminal.

Any help getting this resolved would be wonderful!

---

### Post by earthmeLon on 2011-01-24
*sigh*

Seems that I'd forgotten to modify the SERVER's '/etc/ssh/sshd_conf'.
Within that file is the option ClientAliveInterval.  I uncommented that line and changed it to 60.

This seems to have solved my problem.

---

