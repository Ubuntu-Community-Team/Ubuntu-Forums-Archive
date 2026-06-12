---
title: "Arresting shutdown process"
date: 2011-11-18
forum: General Help
---

### Post by userubunt on 2011-11-18
I would like to do this:
when I click  "shutdown" (or reboot)
a script is evoked.
This script have to kill the shutdown process (shutdown -c) and then show a pop up (zenity) like "you realli want to turn off? What a pity!" so when i click "yes" the "shutdown 0" command is given and the system really shutdowns.
I tried to make things like: 
update-rc.d thisscriptitoldyou start 01 1 .
But it does not work. It stops the process when the graphic environment is already off (so it can't display the pop up and so it can not shutdown)

Someone would know how to do?

---

### Post by userubunt on 2011-11-19
Maybe the only way is recompiling the module "shutdown" of the kernel?

---

