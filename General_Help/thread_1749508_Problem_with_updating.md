---
title: "Problem with updating"
date: 2011-05-04
forum: General Help
---

### Post by luisge on 2011-05-04
Hi, I'm new to linux, and i don't know much, but when I tried to update I get this error:


E: Type 'sudo' is not known on line 52 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Can someone please help me??

---

### Post by ted_rmt on 2011-05-04
Sorry. I am a beginner, too.  For others to help you will need to tell them what version of Ubuntu you were using and the version that was chosen for upgrade.

My recent experience upgrading from 10.10 to 11.04 Natty Narwhal was generally good though painfully slow. Only my compiz settings got messed up and Natty refuses to use my Nvidia drivers (activated but not in use) so none of the cool visual effects are available that I had laboriously configured.

You may find that it is much faster to just download the .iso of the Ubuntu version that you want, back up your documents and do a fresh install. 

I timed my install of 10.04 at 36 minutes including restart and downloading drivers. This upgrade took over three hours. I will never do a Ubuntu upgrade again. 

Note, I do not blame Ubuntu. A clean install is preferable to an upgrade with any system if you can swing it.

---

### Post by plucky on 2011-05-04
> **luisge said:**
> Hi, I'm new to linux, and i don't know much, but when I tried to update I get this error:


E: Type 'sudo' is not known on line 52 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Can someone please help me??

Please open a terminal and post output of ```
cat /etc/apt/sources.list
```

---

