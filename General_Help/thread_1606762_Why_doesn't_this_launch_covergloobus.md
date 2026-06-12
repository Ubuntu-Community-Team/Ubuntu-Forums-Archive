---
title: "Why doesn't this launch covergloobus?"
date: 2010-10-26
forum: General Help
---

### Post by bowens44 on 2010-10-26
This script is a slightly modified version of one I found here the forums.
It i supposed to launch covergloobus and banshee and then close covergloobus if I close banshee.

Can someone tell me why this doesn't work?
It does launch banshee  but not covergloobus

If I do python /usr/share/covergloobus/covergloobus.py in a terminal it runs covergloobus

#!/bin/bash
python /usr/share/covergloobus/covergloobus.py &
CoverGloobusPID=$!
banshee-1 --redirect-log --play-enqueued %U
kill $CoverGloobusPID

thanks

---

