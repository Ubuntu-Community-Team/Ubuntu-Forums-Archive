---
title: "Run scrot (terminal program) to take screenshots in background when user logs in"
date: 2011-01-19
forum: General Help
---

### Post by stnrwd on 2011-01-19
I have a script that looks like this.

```
#!/bin/bash
watch -n 4 scrot %d-%m-%y-%H-%M-%S-dmp.jpg -u -q 20
```

This basically repeats 'scrot ...' every 4 seconds. I want this to execute when a user logs in. Adding the script to startup applications does nothing, as it appears it must be run in a terminal. (The same goes with adding it to usr bin etc, and simply calling it with ie alt-f2 does nothing either.

Any suggestions?

---

