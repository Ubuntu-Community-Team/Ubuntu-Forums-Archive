---
title: "Tell a specific file how to run?"
date: 2011-04-01
forum: General Help
---

### Post by RobotGymnast on 2011-04-01
I have a specific shell script file which I'd like to run in a pop-up terminal every time it's used, but most shell scripts I have can simply be run without the terminal. Is there a way to specify that I want only this script to run with gnome-terminal, but any other shell script should just be run normally?

---

### Post by lithopsian on 2011-04-01
Are you running from a menu/icon or from the command line?  In the first case, simply change the command to invoke the terminal with the script to be executed.  In the second case, create a script that runs a terminal to invoke the first script.

---

### Post by RobotGymnast on 2011-04-01
> **lithopsian said:**
> ...create a script that runs a terminal to invoke the first script.

I just modified the script to include (at the beginning)

```

gnome-terminal -x 

```

Thanks

---

