---
title: "Help with mv script please"
date: 2010-10-16
forum: General Help
---

### Post by joshpond on 2010-10-16
Hi all,

This is a repost from the multimedia forum as I couldn't get any help so maybe in the wrong place.

Currently running mythbuntu 10 and I'm trying to write a script that will move the *.mpg recording onto my server when it has finished recording. It is automated so I need it not to prompt for the password.

This is what I have so far:

1) System events, when finished recording: /var/lib/mythtv/mover.sh

2) mover.sh (chmod +x)
```

#!/bin/sh
#this is to move the files after recording locally
#to a unRaid box (reiserfs conflict)
sudo mount {server ip address}:/mnt/cache/  /mnt/pvr
sudo mv /var/lib/mythtv/recordings/*.mpg /mnt/pvr

```

3) sudo visudo
```

{name of pc} All = NOPASSWD: /var/lib/mythtv/mover.sh

```

This is my first script and I don't know too much so go easy, but I'm not sure what I'm missing. 

Thanks Josh

---

### Post by joshpond on 2010-10-18
Does anyone have any suggestions?

Is my coding for the script correct?

Thanks Josh

---

