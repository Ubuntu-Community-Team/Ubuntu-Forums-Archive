---
title: "Opera 12.00 does not launch in Ubuntu 12.04 64 bit LTS"
date: 2012-07-14
forum: General Help
---

### Post by Welly Wu on 2012-07-14
Hi.

I am having problems with Opera 12.00 on my System76 Lemur Ultra running Ubuntu 12.04 64 bit LTS. It does not launch at all unless I invoke the sudo opera command. I did a search on Google and I found that I have to change the ownership of the ~/.kde hidden folder as it is currently owned by the root to make Opera 12 work on Ubuntu 12.04 64 bit LTS. So, I typed in sudo chown -R wellywu:wellywu ~/.kde and Opera 12 still does not work.

Can someone help me to make Opera 12 launch and work properly?

---

### Post by Karlchen on 2012-07-14
Hello, Welly Wu.

Are you using Ubuntu 12.04 with KDE or with Gnome or with Unity interface?
Unless you are a KDE user changing the owner of any .kde folder and its content is unlikely to fix any Opera 12 startup issues.

I suggest two things:
Use Synaptics and uninstall Opera 12, next re-install it.
In case this does not make Opera startup correctly, execute these commands ```
cd
mv .opera .opera.backup
``` Try to launch Opera again.
In case it starts up properly now, your current Opera profile was broken.

In case both steps do not help, please, launch Opera from the commandline and post the screen output here: ```
cd
opera
```Kind regards,
Karl

---

### Post by Welly Wu on 2012-07-14
Your solution worked. Opera 12 is now running in Ubuntu 12.04 64 bit LTS in the Unity 3D desktop environment.

Thank you.

---

### Post by Karlchen on 2012-07-14
Hello, Welly Wu,

glad to learn my advice was helpful and your Opera starts up fine now.

Cheers,
Karl

---

