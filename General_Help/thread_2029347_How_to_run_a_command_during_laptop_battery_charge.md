---
title: "How to run a command during laptop battery charge"
date: 2012-07-19
forum: General Help
---

### Post by GrzesiekC on 2012-07-19
Hello,

I'd like to run some scripts during laptop battery charge. When the battery is full I'd like to stop those scripts. As for now I only found how to run scripts during online/ofline operations with pm-utils:

#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        # enter your commands here
    ;;
    false) ### laptop enters ac mode
        # enter your commands here
    ;;
    *) exit ;;
esac


Is there something similar for charging ?
Cheers
Gregory

---

