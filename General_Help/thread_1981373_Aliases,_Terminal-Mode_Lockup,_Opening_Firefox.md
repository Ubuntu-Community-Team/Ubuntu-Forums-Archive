---
title: "Aliases, Terminal-Mode Lockup, Opening Firefox"
date: 2012-05-16
forum: General Help
---

### Post by julianloui on 2012-05-16
(1) Making Linux Aliases Permanent:
 I realize that aliases created on the command line are effective only during the current session. However, no matter whether I store my own  aliases in /root/.bashrc or /home/.bash_aliases as suggested by Linux, Linux seems oblivious to the presence of my aliases in these files. Rebooting or restarting Linux does not help.

 (2) Terminal-Mode Lockup:
 Is there any sure-fire way to return Ubuntu Linux from terminal mode to desktop mode? This morning I found myself unable to get back to desktop  mode from terminal mode via CTL+ALT+F7. I was locked in terminal mode  regardless what else I did. 

 (3) Invoking Firefox or Any Other Website via Command Line:
 Is there a terminal command to open Firefox or any other website? I can do that with a simple MSDOS command under Windows XP.

Julian

---

### Post by m_duck on 2012-05-16
1) You'll want to stick the aliases in /home/**username**/.bashrc (or /home/**username**/.bash_aliases - this is sourced by .bashrc by default in Ubuntu).

2) Not completely sure of the scenario - what caused you to be dropped to a TTY? Was X still running or had it stopped?

3) You can run Firefox (or any application in your $PATH variable) just by typing the application name into a terminal. For Firefox, if you wanted to open Google, use something like:```
firefox www.google.co.uk
```or if an application is not in your $PATH:```
/usr/bin/firefox www.google.co.uk
```(Note /usr/bin will be in your $PATH (or should be)).

---

### Post by Habitual on 2012-05-16
> **julianloui said:**
> (1) Making Linux Aliases Permanent:
 I realize that aliases created on the command line are effective only during the current session. However, no matter whether I store my own  aliases in /root/.bashrc or /home/.bash_aliases as suggested by Linux, Linux seems oblivious to the presence of my aliases in these files. Rebooting or restarting Linux does not help.

I have a few too many myself, but I keep them organized in separate files sourced via **my** ~/.bashrc like so 
```

source /home/jj/.aliases
source /home/jj/.c9ssh

```
Substitute your userid for jj, I'll assume julian below...

Be certain to add 
```
alias reload='source ~/.bashrc'
``` to /home/julian/.aliases
After saving /home/julian/.aliases, either in an open terminal (or open a new one) and type
```
source ~./.bashrc
```

Now any changes to any of your .bashrc, or your .aliases files (edits) can from then on be "reloaded" in terminal by typing "reload" in terminal.

Have a look at
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by julianloui on 2012-05-18
Hi, m_duck,

1) Thanks for your good instructions.  I stuck a few aliases in the alias file last night to save future work. 

2) I think my Ubuntu 12.04 just happened to have crash and was frozen solid when it was in terminal mode.  My only way out was to shut off the computer.

3) I tried both of your Firefox-command suggestions. In each case, Linux returned "No Display Specified".  Have you experienced such a problem before?

[--- 2012-05-23:  Problem Solved ---]  This problem was caused by my using Ctl+Alt+F1 instead of Ctl+Alt+T to launch the command line.  I learned today that 
the Ctl+Atl+Fx keyboard commands are not attached to or related to Display X in any way.
   
Thanks again.

Julianloui

---

### Post by julianloui on 2012-05-19
Hi, Habitual,

Thank you very much for your very comprehensive advice on aliases as well as the the excellent URL [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108). It contains such a wealth of Linux knowledge.  I've just downloaded one of the PDF books.  I look forward to digging into it and the other volumes.  They should keep me busy for a long time.

Julianloui

---

