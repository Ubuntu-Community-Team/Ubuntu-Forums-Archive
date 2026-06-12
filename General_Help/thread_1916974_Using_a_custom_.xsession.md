---
title: "Using a custom .xsession"
date: 2012-01-29
forum: General Help
---

### Post by lourensc on 2012-01-29
I could not get the .xsession in my home directory to run during startup.  dr_willis on the irc channel directed me to the man page for Xsession.  Based on the info there I devised the following plan:

Create ```
/etc/X11/Xsession.d/41custom_run-user-xsession
``` with:
```

if [ -r "$USERXSESSION" ]; then
  $USERXSESSION &
fi

```Make it and the .xsession script in the home directory executable.
```

chmod +x ~/.xsession
sudo chmod +x /etc/X11/Xsession.d/41custom_run-user-xsession

```Now one can call  scripts that should run on login from ~/.xsession file.  Mine looks like this.  

```

#!/bin/bash

~/bin/capsgone

```Regards 

Lourens

---

