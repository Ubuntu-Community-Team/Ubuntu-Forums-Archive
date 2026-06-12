---
title: "No Desktop environment after removing teamviwer"
date: 2012-04-13
forum: General Help
---

### Post by JCM_Pico on 2012-04-13
Hi  there I've no desktop environment after apt-get remove teamvier7... and can't understand whats missing... 
Any suggestion of how to fix this?

---

### Post by raja.genupula on 2012-04-13
to where you are booting ? 

how your system booting ? please explain .

EDIT: i came through this [http://ubuntuforums.org/showthread.php?t=1957317](http://ubuntuforums.org/showthread.php?t=1957317)

---

### Post by JCM_Pico on 2012-04-13
Im logging in in console mode... Its the only choice i have

---

### Post by abyrne on 2012-04-13
Are you able to reach any sort of graphical login screen? What version of Ubuntu are you running? Do you recall the "apt-get remove" command mentioning anything about Xorg?

---

### Post by JCM_Pico on 2012-04-13
> **abyrne said:**
> Are you able to reach any sort of graphical login screen? What version of Ubuntu are you running? Do you recall the "apt-get remove" command mentioning anything about Xorg?

No I can't get to any graphical login... Im  Ubuntu 10.04... And when I runned the apt-get command i havent seen any critical pacoaged being removed... This problem may also be related to the last system update... But the only thing I remember that sãs in the update list was samba...

---

### Post by raja.genupula on 2012-04-13
```
sudo apt-get install --reinstall ubuntu-desktop
```

after login from console do that

---

### Post by JCM_Pico on 2012-04-13
> **raja.genupula said:**
> ```
sudo apt-get install --reinstall ubuntu-desktop
```

after login from console do that

It did nothing... Got the same problem

---

### Post by abyrne on 2012-04-13
Hmm. Are you booting using recovery mode? Or are you just booting normally but getting no graphics?

---

### Post by JCM_Pico on 2012-04-13
The second one :(

---

### Post by abyrne on 2012-04-13
Could you post your Xorg log and your dmesg log? Both are located in /var/log/.

---

### Post by JCM_Pico on 2012-04-13
I've attached the log files.... after the edit

---

### Post by raja.genupula on 2012-04-14
> **JCM_Pico said:**
> The second one :(
from recovery mode if you choose failsafeX mode , what are you getting ?  if it takes to GUI  FailsafeX please reinstall your graphics drivers once .

---

### Post by JCM_Pico on 2012-04-14
> **raja.genupula said:**
> from recovery mode if you choose failsafeX mode , what are you getting ?  if it takes to GUI  FailsafeX please reinstall your graphics drivers once .

I get a very fast dump... Can't read it... And no GUI :(

---

