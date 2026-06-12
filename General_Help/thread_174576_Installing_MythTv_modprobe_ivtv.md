---
title: "Installing MythTv: modprobe ivtv"
date: 2006-05-12
forum: General Help
---

### Post by burnt1ce85 on 2006-05-12
I'm following a "how-to install mythtv on ubuntu" guide and im have a little of bad luck.

I am presented a task to install a module with the command:
**modprobe ivtv**

Though i get an error saying this:
**FATAL: Module ivtv not found.**

Im not sure exactly why the module cannot be found. I followed the guide step by step without any problems. The guide can be viewed [here]("http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html").

Thanks. P.S. I'm sort of a newbie. I have worked with linux in labs for 3 years now  but i dont have much experience installing linux software.

---

### Post by brossatscu on 2006-05-12
Ubuntu isn't seeing the module, if you already have it installed. You either need to register the module (read up in the module docs for ivtv about this) or try 'depmod -a' before you 'modprobe ivtv'

---

