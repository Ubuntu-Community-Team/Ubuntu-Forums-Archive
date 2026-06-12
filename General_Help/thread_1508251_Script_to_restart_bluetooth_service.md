---
title: "Script to restart bluetooth service"
date: 2010-06-12
forum: General Help
---

### Post by airtacable on 2010-06-12
Hey guys,

Hope you're all well. I have a problem with my bluetooth - not sure if  it's Ubuntu or the dongle: it doesn't seem to be starting properly  during the startup. The bluetooth icon appears in the task bar with a  red x in the bottom right and nothing can be connected to the PC. To get  it to work, I have to either plug out and plug in the dongle or restart  the bluetooth service in the terminal:

```
/etc/init.d/bluetooth restart
```I tried to put this in a script that would run at start up as a work around to the problem, but it's not working.

```
#!/bin/bash

/etc/init.d/bluetooth restart
```I'm a novice at bash, so I could be way off the mark.

Any ideas?

---

