---
title: "Running Script on Program Close"
date: 2010-03-08
forum: General Help
---

### Post by squirrelplayingtag on 2010-03-08
I'm trying to make a script that will copy over the settings file for firefox everytime firefox is closed. What would be the best way to go about doing this.

---

### Post by gmargo on 2010-03-09
The only sensible way is to wrap firefox in a shell script.  Try this: Create a file called $HOME/bin/firefox.
Content of that file:
```

#!/bin/sh
/usr/bin/firefox $*

# now your clean up tasks
....


```As long as $HOME/bin is in your $PATH (before /usr/bin), the next time you start firefox, it should run the one in $HOME/bin instead of /usr/bin.

---

### Post by squirrelplayingtag on 2010-03-10
Nice, works perfectly. Thanks

---

### Post by gmargo on 2010-03-10
I realized that there's a problem with my method.  One can run the "firefox" command even after firefox is already running, in which case the existing firefox is used, and a new window is opened.  So the clean up portion would run too often.

There is a "lock" symbolic link created in the profile directory, which could be tested to see if firefox has really exited, something like this:

```

#!/bin/sh
/usr/bin/firefox $*

# Fill in your own path to the firefox profile directory
PROFILE=/home/gmargo/.mozilla/firefox/jrg21kgo.default
LOCK="$PROFILE/lock"

# Only run clean up if lock is gone
if [ ! -L "$LOCK" ]; then
    # now your clean up tasks
    ....
fi


```

---

