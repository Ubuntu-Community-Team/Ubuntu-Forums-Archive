---
title: "Rsync not working as intended on Maverick"
date: 2010-11-25
forum: General Help
---

### Post by jim.webguru on 2010-11-25
Hello,

I have a pc that i have upgraded Ubuntu from version 9.10 to 10.04 to 10.10. Now, in Maverick I can not get rsync to work correctly. The delete option does not work and updated files in the source do not get recreated in the destination. Can someone tell me if I'm doing something wrong:

My rsync command and output:

rsync -r -t -v --progress --delete /media/ProDrive2/source /media/destination

sending incremental file list

sent 6122 bytes  received 14 bytes  12272.00 bytes/sec
total size is 55193674519  speedup is 8995057.78
Rsync process exit status: 0

---

### Post by jim.webguru on 2010-11-25
Nevermind. It was something I over looked. Ugggghhhh. It's creating a new folder. Geez.

---

