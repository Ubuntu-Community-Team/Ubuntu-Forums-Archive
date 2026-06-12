---
title: "Command works in terminal but not on quicklaunch button"
date: 2010-11-24
forum: General Help
---

### Post by john1923 on 2010-11-24
Hi 

I want to limit my non-work internet browsing so I have written a command that when pasted into a terminal will open a browser, wait 10 sec then kill the browser

> /usr/bin/opera %U & sleep 10; killall operaThis works perfectly if pasted into a terminal. However I want it to work on one of the quick-launch buttons.

When I alter the command in the quick-launch button to contain the above command it no-longer kills opera.

Do you know why this is the case? and can you help fix it?

Thankyou in advance

---

### Post by endotherm on 2010-11-24
launchers won't let you put in multiple commands, so tehre are a couple workarounds:
1) put the command in a script file, and have the launcher invoke the script (my preference)
2) put this in the launcher
```

bash -c "/usr/bin/opera %U & sleep 10; killall opera "

``` so that the command is a single invocation of bash (that happens to do other stuff too). regards to whomever showed that to me last week.

---

### Post by DaithiF on 2010-11-24
the ability to chain multiple multiple commands with a ';' is a shell feature, when invoking a command from a launcher you're just launching that command, but not necessarily via a shell.  so put your commands in a script with #!/bin/bash as the shebang, and invoke that script from your launcher.

---

### Post by john1923 on 2010-11-24
Thank you endotherm and DaithiF.

that makes perfect sense, you've solved my problem. Now I will change the timer to give me more than 10 seconds of web browsing.

---

