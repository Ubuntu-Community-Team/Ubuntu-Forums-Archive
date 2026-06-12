---
title: "sudo/gksudo + internet access"
date: 2012-06-19
forum: General Help
---

### Post by MindyErbiznez on 2012-06-19
Hi
I'm having an issue with Ubuntu 10.04 LTS where unless the machine is connected to the internet sudo & gksudo doesn't work.  by doesn't work i mean on a console, I type: sudo <any executable>
and the console tries to run the command then fails without the usual prompts.
however, if the machine is connect to the internet, typing: sudo <any executable>, doesn't the usual prompt for password, then runs the command successfully.

any ideas about what's happening?
what log files should i look at to see what's going on?

thanks!

---

### Post by HiImTye on 2012-06-19
I'd look at both 'kern.log' and 'auth.log'

---

### Post by MindyErbiznez on 2012-06-20
Thanks for the reply.
I checked both kern.log and auth.log but neither seem to have any relevant messages.

Any other suggestions?

---

