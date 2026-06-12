---
title: "Remote Shutdown"
date: 2010-03-17
forum: General Help
---

### Post by KdotJ on 2010-03-17
Hey guys,
Is there a command to remotely shutdown a computer on the local network? I have a computer running as a file/print server and I have no screen or keyboard connected to it. Would be great if I could shut it down from my laptop. I have the needed credentials (as I'm guessing these would be needed in the command?)

thanks in advance

---

### Post by llamabr on 2010-03-17
You mean you can ssh into it, and you want to shut it down?  There's the shutdown command:

sudo shutdown -h now

---

### Post by KdotJ on 2010-03-17
Cool thanks, I'll give that a try. 
As for ssh I don't think... I mount the shares to a folder in my /home directory. I'm not too clued up on connecting through my network via linux...

[edit]
The server isnt actually running the ubuntu server edition. It just the normal version running samba on it
(if this makes a difference.)

---

