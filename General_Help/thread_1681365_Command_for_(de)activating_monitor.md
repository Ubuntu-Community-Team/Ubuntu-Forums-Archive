---
title: "Command for (de)activating monitor"
date: 2011-02-04
forum: General Help
---

### Post by belnac on 2011-02-04
Hi,

Title of thread says it all really. Is there a way to issue a command in a terminal to activate/deactivate a monitor in twinview (or dual head)? 

It's just that I'd love to have a simple script I could run from the command line instead of having to go to nvidia-settings each time I need to make a activate/deactivate a monitor.

---

### Post by tredegar on 2011-02-04
**nvidia-settings** can be run from the command line.
Please see man **nvidia-settings** for how to save and load an nvidia settings file.

Set up two files with the different configs you want.
Then set up two GUI launchers to load the configurations you want. Or just make a menu entry that calls the appropriate command [ eg ```
nvidia-settings  -l  --config  ~/.NvidiaConfig-1
``` 

Please let us know how you get on.

---

