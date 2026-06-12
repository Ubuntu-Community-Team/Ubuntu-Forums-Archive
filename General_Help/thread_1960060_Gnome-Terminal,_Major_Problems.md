---
title: "Gnome-Terminal, Major Problems"
date: 2012-04-16
forum: General Help
---

### Post by kman2949 on 2012-04-16
*I could not select the prefix for this message without holding down the cursor and using the down arrow* I am running Ubuntu Linux 11.10 on my Dell Studio laptop. Earlier today I  went to run the gnome-terminal and was surprised to find that when I  clicked on it to run it would open extremely briefly and then close. I  found a thread that suggested entering what I think was the command "metacity  --reinstall" in xterm and that command appears to have removed all  sidebars/ways to run any program. Also, right after entering the "metacity --reinstall" code about 10 terminals opened up at once and I exited out of all of them. I could really use some help on this  because I am supposed to be using this computer for work purposes. Thank  you very much.

---

### Post by Fwission on 2012-04-16
did you try to reset the computer after this happened? Usually after reinstalling a major component your desktop might look messed up

---

### Post by kman2949 on 2012-04-16
Yeah I just restarted the computer and that took care of the side bar and accessibility issues, but the terminal is still acting the same.

---

### Post by daslinkard on 2012-04-16
Are you able to utilize the command line at all to do the following sudo command?

```
sudo apt-get remove gnome-terminal
```

and then re-install gnome terminal by doing

```
sudo apt-get install gnome-terminal
```

---

### Post by daslinkard on 2012-04-16
Next question....check out this [post]("http://ubuntuforums.org/showthread.php?t=1768967") as it seems that this post might pertain to you....let me know what you find out.

---

