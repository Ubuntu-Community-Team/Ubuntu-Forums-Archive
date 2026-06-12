---
title: "Gnome and ssh-agent ."
date: 2009-07-29
forum: General Help
---

### Post by VeskoJl on 2009-07-29
Is there a way to unlock ssh keys automatically when i log in, so don't have to type every key password?
 I thought this is the default way ssh-agent works, but I've installed seahorse and sshmenu and there is two key agents (ssh-agent , seahorse-agent), so i'm not sure if this is from messed up settings, or default way ssh-agent works.

---

### Post by Johnny B on 2009-07-29
can you just use a blank password for your keys?
thats how i do it.

---

### Post by VeskoJl on 2009-07-29
Yes, I could. But with an old build of Jaunty i've used ssh-agent following way, just log in and then gnome-keyring (not sure) asks for 1 password and don't have to  type every key pass.

This thread seems relevant [link]("http://ubuntuforums.org/showthread.php?t=1145017")

 
P.S. It's very frustrating that it's impossible to configure Ubuntu like previous install.

---

### Post by VeskoJl on 2009-07-29
Problem solved. Make sure you can unlock default (login) keyring, if not follow [this]("http://ubuntuforums.org/showthread.php?t=1224894&highlight=login+keyring").

---

