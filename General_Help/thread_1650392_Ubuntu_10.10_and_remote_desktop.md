---
title: "Ubuntu 10.10 and remote desktop"
date: 2010-12-21
forum: General Help
---

### Post by Blastnsmash on 2010-12-21
How do you configure the remote desktop to listen to localhost only?

I've looked for a configuration file but haven't been successful. Any help? I also noticed in previous version of unbunbtu (I misspelled ubuntu but thought it was so hilariously misspelled i'm going to leave it.) there was an advanced tab that you could set this property. But there isn't an advanced tab for the remote desktop anymore?

Any help greatly appreciated. 

Basically, I have ally my services run local only and then use ssh. When I port scan ubuntu from another computer I want to see one service only - SSH.

---

### Post by pricetech on 2010-12-21
Is turning off remote desktop not an option ??

---

### Post by Verbeck on 2010-12-21
edit:wrong thread
edit 2: try [ufw]("https://help.ubuntu.com/community/UFW") to deny that port

---

### Post by Blastnsmash on 2010-12-21
> **Verbeck said:**
> edit:wrong thread
edit 2: try [ufw]("https://help.ubuntu.com/community/UFW") to deny that port

That will certainly work but I'd rather just edit the config file for vnc server and say hey listen to localhost only. It's that easy with mysql :P

---

