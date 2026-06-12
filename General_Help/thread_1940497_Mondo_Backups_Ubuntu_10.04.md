---
title: "Mondo Backups Ubuntu 10.04"
date: 2012-03-13
forum: General Help
---

### Post by gachnar on 2012-03-13
Looking to make a backup of my server using the backup Mondo. I get it installed and running perfectly when I try to run it manually, but if I try to automate it via cron.... There's the rub, it won't run. I don't see any processes, cron shows that it executed the sh script, but no action. Does anyone have any ideas?

To start off script located
/usr/local/sbin/mondo.sh

script permissions
777

script ownership
root:root

added to cron via root crontab

mondo.sh contents
```

#!/bin/sh
mondoarchive -Oi -d /var/images -E /var/images -s 4200m

```

Any ideas? I'd love to automate this if possible, but I'm running into a block and the documentation on their website doesn't seem to be updated since well, forever. Thanks for the help and please post if you need any more information.

EDIT:
I just realized that I didn't show my crontab

Crontab -l
30 21 * * * /usr/local/sbin/mondo.sh

To my understanding that should run nightly at 21:30 or 9:30PM. Does anyone have an idea to help here?

---

