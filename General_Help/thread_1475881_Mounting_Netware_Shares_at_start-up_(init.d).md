---
title: "Mounting Netware Shares at start-up (init.d)"
date: 2010-05-07
forum: General Help
---

### Post by MalachiConstant on 2010-05-07
Hi all,

I can mount Netware shared folders with ncpmount at work. The command works fine. Now, I want the folders to be mounted automatically at start-up. So I put this script in /etc/init.d and configured it with rc-update:

#!/bin/bash

touch /etc/init.d/touched_by_an_angel

ncpmount -A XXXXX.de -S XXXX -V XXXX -U XXXX.fb14.uni-hamburg -P XXXX -u janus /home/janus/novell


When I execute the script from the command line it creates the file touched_by_an_angel and mounts the folder. However, at start-up, the folder is not mounted, but the touch command is still being executed.

Maybe the script is run too early (before the network connection is established)? Any help would be appreciated!

Thanks,
 Janus

---

### Post by MalachiConstant on 2010-05-10
Any suggestions?

---

### Post by MalachiConstant on 2010-05-19
I'm still stuck with this. Has anyone gotten it to work?

---

