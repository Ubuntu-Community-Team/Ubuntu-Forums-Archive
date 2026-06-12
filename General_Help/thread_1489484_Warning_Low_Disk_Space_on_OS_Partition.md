---
title: "Warning: Low Disk Space on OS Partition"
date: 2010-05-21
forum: General Help
---

### Post by mgco on 2010-05-21
Hello forum,

I'm trying to free up some space on the 4GB partition of my netbook since I've been receiving these warnings that I have NNN_MB left as free space. So what I did was to remove programs (via Ubuntu Software Center) that I thought wasn't that a priority for me.

But, there seems to be no change! Am I doing something wrong? The warnings keep coming.

Now that I'm thinking of upgrading to Lucid Lynx, I'm not too sure if I can.

Thank you

---

### Post by dcstar on 2010-05-21
> **mgco said:**
> Hello forum,

I'm trying to free up some space on the 4GB partition of my netbook since I've been receiving these warnings that I have NNN_MB left as free space. So what I did was to remove programs (via Ubuntu Software Center) that I thought wasn't that a priority for me.

But, there seems to be no change! Am I doing something wrong? The warnings keep coming.

Now that I'm thinking of upgrading to Lucid Lynx, I'm not too sure if I can.

Thank you

Delete old log files and clear the cache through Synaptic.

---

### Post by R3VAMP3D on 2010-05-21
Easier way, delete rotated logfiles in /var/log, (ones with a number in the filename) and run sudo apt-get clean in a terminal.

---

### Post by Rasa1111 on 2010-05-21
in Terminal
sudo apt-get autoclean
sudo apt-get clean

also,
open synaptic, 

click "status" in the bottom left column, 
then, in the top left column, click, "Not Installed (residual config)"
and those are all things taking space for no reason. 
you can mark them for complete removal. 

 that should free up some space for you.

---

### Post by mgco on 2010-05-25
thanks for this.. will try them soon

---

