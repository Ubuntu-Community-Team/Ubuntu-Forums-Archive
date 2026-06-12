---
title: "My custom bash alias won't work from those &quot;command line bars&quot; on panel"
date: 2009-10-07
forum: General Help
---

### Post by rob86 on 2009-10-07
I'm not sure what you call those things, but I mean those things on your desktop panel that let you type in commands. I made a custom bash alias that downloads an image (weather) and opens it up, and I thought it would work if I typed it in the panel box, but it says Could not execute command. 

Is it because these panel things weren't meant to do stuff like that and are just meant for starting a program?

---

### Post by unutbu on 2009-10-07
Okay, for whatever reason the command line bar in the panel does not recognize aliases. How about change your alias into a little script? For example, if your alias is
```

alias ll='ls -l'
```

Then just make a file called ~/bin/ll:
```

#!/bin/bash
ls -l
```

Make it executable:
```

chmod +x ~/bin/ll
```

and you should be all set. 

PS. If you do this, you should probably remove the alias from your .bashrc so there is no confusion about which one the shell is executing.

---

### Post by OpenGuard on 2009-10-07
Bash .. Are we talking about shell scripts ( .sh ) ? If so, move it to /usr/local/bin and you should be able to launch it from wherever you want.

---

