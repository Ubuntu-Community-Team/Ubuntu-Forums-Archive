---
title: "Ubuntu 11.10 hangs"
date: 2011-11-14
forum: General Help
---

### Post by shrek1 on 2011-11-14
I have Ubuntu 11.10 installed on my dell vostro. I uses WiFi connection to connect internet. 

Sometimes my system hangs automatically.  and  after  that  only some   general  application  and  commands works , when i type sudo  on  terminal  cursor starts blinking over there, without returning   the   prompt, then to terminate it i have to use force quit to terminal. also  my WiFi disconnects  automatically  but     logo shows that it is connected , but   when i try to disconnect it   manually   nothing happens. 
when  i shutdown my computer  then following  error shows on boot screen   : 
modem-manager:caught signal 15                           [Fail]
i have to use force shutdown button.                                    

Please reply because it happens many times in a day, my hard-drive can crash.

---

### Post by Blackbug on 2011-11-14
have you installed any of the modem drivers which ubuntu detects after the fresh installation.
if yes try reinstalling it. apart from that are you using ubuntu default network manager or any other ( for eg. Wicd )?
 
you can check ```
dmesg
``` for kernel logs and may be some more information for this problem could be traced out..

---

### Post by shrek1 on 2011-11-14
yes, i am using Wicd. i haven't installed any modem-driver and which word should i grep for dmesg output?

---

### Post by wowcolombia1 on 2011-11-14
You are new with Ubuntu?
If you are maybe its a problem with drivers(that is what i think)or maybe you did something that causes those errors,if i was you a did a installation of Ubuntu again.Then enjoy it :popcorn:

---

