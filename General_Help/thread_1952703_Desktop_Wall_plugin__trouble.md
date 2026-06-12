---
title: "Desktop Wall plugin  trouble"
date: 2012-04-04
forum: General Help
---

### Post by achu91 on 2012-04-04
hello ,
i am new to Ubuntu and using Ubuntu 11.10 .Due to my inquisitiveness i opened ccsm and enabled desktop wall plugin .it showed many conflicts problem and i ignored the same and  just clicked on green button showing tick mark assuming nothing will go wrong.But to my surpise i found after enabling the plugin  that in desktop my unity pannel and top pannel missing .i cannot open any application /shut down button.but  i can open only the files present in the desktop.

Den i some how how boot through recovery mode and posted this question.

Can anyone help to solve my issue or how to reset the desktop or access ccsm so that i can change the settings.i had enabled auto login. 

pls reply

---

### Post by Paddy Landau on 2012-04-05
[LIST=1]
[*]Boot normally into Ubuntu.
[*]Press Ctrl-Alt-T to open a terminal.
[*]Type the following and press Enter:```
unity --reset
```
[*]Wait. This could run for several minutes. If it appears to hang for more than 10 minutes, close the terminal.
[*]Reboot.
[/LIST]
Compiz is a complicated piece of software and, if you don't know what you're doing, you can easily mess it up.

To play around with Compiz, always back up your current settings before continuing: Preferences > Export. That way, if you have to reset (as above), you can restore your last-working settings and try again: Preferences > Import.

---

### Post by achu91 on 2012-04-05
thank you very much,i tried as u told waited for morethan 10 min ,and there was no response showing "unable to find file "
then i closed the terminal and rebooted. it worked well.

Thanks a lot.

---

### Post by Paddy Landau on 2012-04-06
That's good.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

