---
title: "Show current commands in Terminal"
date: 2010-01-06
forum: General Help
---

### Post by huviduc on 2010-01-06
I was wondering if there was a way to show all current actions i am doing in a terminal window? For example if i left a terminal window open on one of my desktops, could i make it display everything I am doing so that when i receive some general error in a program, I could jump over and get some more details. I could also use it to see what commands are actually run when I do certain things. Hopefully you can get an idea of what im looking for, thanks.

---

### Post by bodhi.zazen on 2010-01-06
Not really.

The closest you can come would be to open a terminal and use screen.

You can then start your graphical apps from the command line.

You could, if you wish, redirect output from your commands into application specific files.

In terms of system errors , this is what logs are for

```
tail -F /var/log/messages
```

---

