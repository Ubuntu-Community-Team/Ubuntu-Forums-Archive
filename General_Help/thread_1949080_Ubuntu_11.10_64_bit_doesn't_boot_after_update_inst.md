---
title: "Ubuntu 11.10 64 bit doesn't boot after update installation"
date: 2012-03-29
forum: General Help
---

### Post by jucestain on 2012-03-29
Today I installed like ~10 updates (They were released today). Not exactly sure what they were but I usually just install updates whenever the update manager prompts me to do so. Anyhow, I reboot after installing the updates and now my computer won't get past the purple screen. Im able to login via ctrl-shift-f1 and my files are still there. But, I can't get to the regular login screen. 

I think the updates mucked with the graphics drivers somehow. I changed quietsplash to nomodeset and the comp still doesn't get to the login screen. Any suggestions? Thanks.

Just fyi im using a 580gtx with nvidia drivers 285.05.33.

---

### Post by mikewhatever on 2012-03-29
You probably just need to reinstall the Nvidia driver. That's the disadvantage of installing it manually, you have to reinstall it after kernel updates.

---

### Post by raja.genupula on 2012-03-29
yup +1 . 

In the grub menu , choose Recovery option and then boot with failsafeX mode to reinstall your Drivers .

and have a eye for a useful technique of auto updation of Graphic drivers . 

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

hope that helps.

---

### Post by jucestain on 2012-03-29
Guys,

This worked. Thanks.

---

### Post by raja.genupula on 2012-03-30
Yeah now please mark your thread as solved from thread tools . 
Thank you .

---

