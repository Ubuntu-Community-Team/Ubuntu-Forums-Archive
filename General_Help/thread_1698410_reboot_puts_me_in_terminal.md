---
title: "reboot puts me in terminal"
date: 2011-03-02
forum: General Help
---

### Post by haya on 2011-03-02
Although I have been using Ubuntu for a while, I am still  a beginner.  This is the second time that it has happened to me and  I am unable to find a possible solution in my books on Linux and Ubuntu.

Twice I have downloaded updates from Update Manager which required a reboot.  Each time I have rebooted,terminal window has opened. I am unable to get out of terminal to the desktop or to enter any other program ( like office,etc).  I know that the graphics are still in place as The Ubuntu 10.10 screen flashes on before the terminal black screen appears.(I am in runlevel 2 )

A. How can I get out of terminal and onto desktop?

B.  How can I get start up to go the desktop screen and not terminal?

---

### Post by ghostborg on 2011-03-02
It's been a while for me, try startx from the terminal.

Another is: start gdm
might have to use sudo

You should be able to choose from Grub an earlier kernel.

---

### Post by seawolf167 on 2011-03-02
The two commands to try first are

```
startx
```

and

```
sudo service gdm restart
```

---

### Post by haya on 2011-03-03
Thank you for your help.  Although it didn't solve the problem, it led me to the solution. The restart gave me an error that nvidia was not working. That's when I realized that I had disabled nouveau in order to enable nvidia.  The reboot had re-activated nouveau which caused a conflict between the programs thereby moving me into terminal.  The solution was to re-disable nouveau and re-install nvidia.

---

