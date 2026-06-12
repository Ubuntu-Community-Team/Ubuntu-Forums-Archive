---
title: "Remote reboot pending..."
date: 2009-11-09
forum: General Help
---

### Post by dargaud on 2009-11-09
Hello all,
I sometimes want to reboot my ubuntu box while connected via ssh. So I "*sudo reboot -h now*" and a couple seconds later the connection drops, as expected. But it doesn't come back and I can't login anymore. When I walk to the machine, I can see a graphic box that asks something like (from memory): "*there's a ssh/tty connection, do you want to abort*". Heh. How can I skip this ?

---

### Post by whoop on 2009-11-09
> **dargaud said:**
> Hello all,
I sometimes want to reboot my ubuntu box while connected via ssh. So I "*sudo reboot -h now*" and a couple seconds later the connection drops, as expected. But it doesn't come back and I can't login anymore. When I walk to the machine, I can see a graphic box that asks something like (from memory): "*there's a ssh/tty connection, do you want to abort*". Heh. How can I skip this ?

Strange, this works just fine on my machines. What is the version of the ubuntu machine with the ssh service is running on (the machine you are trying to restart)?
Is that machine maybe running a user with elevated privileges?
hhmmm, Just as a test can you run "sudo shutdown -h now" from the ssh terminal and see if that works?

---

### Post by alphaniner on 2009-11-09
You could change 'now' to '+1' and log out of ssh before the machine starts to reboot.  At least it's a workaround until you find a real solution.

---

