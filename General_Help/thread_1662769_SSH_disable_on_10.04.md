---
title: "SSH disable on 10.04"
date: 2011-01-08
forum: General Help
---

### Post by Costas100 on 2011-01-08
I am using Edubuntu 10.04 and all is fine. I have a puzzle regarding SSH disabling.

I started using SSH to transfer files from two of my local computers. Transfers were successful, my problem is on how to disable the SSH server when I do not need it. 

I read that this can be accomplished from the “Services Settings” located under System/Administration The only thing remotely related to to this is the “Startup Applications” under System/Preferences and the only thing there, related to SSH is the “SSH Key Agent”. I suppose I can deactivate it, but I have a hunch this is not the proper solution.

Any chance the “Services Settings” are located elsewhere or maybe there is another method of temporarily disabling the SSH server.

Thank you all

Costas

---

### Post by luvshines on 2011-01-08
I think ```
sudo /etc/init.d/ssh stop
``` should do the trick

---

