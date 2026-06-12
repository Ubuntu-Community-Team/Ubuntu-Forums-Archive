---
title: "Bash script won't run from menu?"
date: 2011-04-13
forum: General Help
---

### Post by bogdarnet on 2011-04-13
Wrote a bash script that works fine when run in a terminal...
Tried to make a shortcut from the application menu to it,
but when I run it from there, I get
"There was an error creating the child process for this terminal."

Any suggestions?

Thanks!

---

### Post by bogdarnet on 2011-04-13
Well, not sure, but maybe it's fixed it to change from "Application in Terminal" to "Application"?  It seemed to run okay after that.

(Not sure why!)

---

### Post by Crusty Old Fart on 2011-04-16
If you want it to open a terminal window, run it as an application in your launcher (as you are doing now) but use: gnome-terminal for the command. Something like this:
```

gnome-terminal --geometry=180x50 -x /path/to/your/script.sh

```

The --geometry=XXXxYY is my custom setting for that option. More options for the gnome-terminal can be found on its man page:
```

man gnome-terminal

```

Hope that helps.

Good luck,

Crusty

---

