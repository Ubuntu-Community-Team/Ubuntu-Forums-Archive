---
title: "rsync, or equivalent, without encryption or ssh"
date: 2009-09-21
forum: General Help
---

### Post by Tralce on 2009-09-21
I'm currently using rsync to sync my home folder from my mac to my two ubuntu machines. The issue is that even though I'm syncing across a 100mbit LAN, I can only get speeds up to 200kB/s. I think it's due to the encryption slowing the transfers down. As such I'm looking for an alternate solution that does not involve encryption and works as well as rsync. Any ideas?

---

### Post by John Cheng on 2009-09-21
rsync does not require SSH. rsync can use the $RSYNC_RSH env variable, which allows you to specify the remote shell. The man page for rsync talks about using the $RSYNC_RSH parameter to switch between ssh and rsh. 

If you are sure that rsync is using ssh as the trasport, you can try installing rshd and use that as the replacement for ssh.

---

### Post by XCan on 2009-09-21
Perhaps before you switch protocol you could try switching cipher since it's so easy? Add ```
 -c arcfour,blowfish-cbc 
``` to your list of ssh flags.

---

