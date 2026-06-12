---
title: "help with port list and end busy port:"
date: 2010-07-21
forum: General Help
---

### Post by magnetpest2k7 on 2010-07-21
Hello All,

Can some one help me with the terminal command to list busy port and a way to kill a port that is being used.

For example when i type netstat -a which gives me Localhost:1110 in listen state now if i have to end the listening port 1110 and make it free how can i do it? 

Thanks
Vin

---

### Post by The Cog on 2010-07-21
The command ```
sudo netstat -pltu
``` will show you the listening ports and the process IDs. Then you can use (e.g.)```
sudo kill -kill 1234
``` to kill that process number.

Anything listening on address localhost can only be connected to by other processes on the same machine, so they are not a security risk.

---

