---
title: "Minimize KAlarm on startup"
date: 2012-05-16
forum: General Help
---

### Post by billstei on 2012-05-16
I use KAlarm, and I had it set to start using the Startup Applications list, but KAlarm does not minimize itself on startup (using the Close Window button, which does not do a Quit), so I use this script to do the job, and then call it from the Startup Applications list.  It requires the xdotool package to be installed:

#!/bin/bash

# Starts KAlarm and then closes the KAlarm window (but KAlarm does not Quit)

# Start KAlarm
kalarm

# Get Window ID, the last one in the list of KAlarm Window processes
WID=`xdotool search --name KAlarm | tail -n 1`

# Activate that window and send Alt F4 to that Window ID to close it
xdotool windowactivate $WID key alt+F4

---

### Post by cmont899 on 2012-05-16
This can be done with devilspie, see here:

[http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html](http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html)

---

