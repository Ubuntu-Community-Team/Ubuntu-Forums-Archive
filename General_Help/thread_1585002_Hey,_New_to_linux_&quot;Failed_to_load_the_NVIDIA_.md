---
title: "Hey, New to linux &quot;Failed to load the NVIDIA kernel module&quot; Please help"
date: 2010-09-29
forum: General Help
---

### Post by dlogan96 on 2010-09-29
Hey, i just recently upgraded to Ubuntu. I also just installed the Nvidia 256.53 drivers for my gtx 460. I did that and it worked fine. But the other day i did some updates that were prompted to me on the desktop. So i did those, then i restart and i got "Failed to load the NVIDIA kernel module." It then asked if i wanted to run in nvidia low graphics mode, which i did. So i am currently trying to figure out how to fix my NVIDIA drivers so that i have 1920x1080. Help would be greatly appreciated since i am very new to Linux.
-Thanks

---

### Post by andrewthomas on 2010-09-29
Have you updated?

```
sudo apt-get update && sudo apt-get install nvidia-current
```

---

### Post by dlogan96 on 2010-09-29
> **andrewthomas said:**
> Have you updated?

```
sudo apt-get update && sudo apt-get install nvidia-current
```

i did that, got "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)" 
"E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

---

### Post by dlogan96 on 2010-09-29
OHHH wait, i just updated like you said, but it had those errors because i had synaptics open. Now its currently downloading something.
what do i do when this is done?

---

### Post by dlogan96 on 2010-09-29
ok, i just restarted, and i didnt get any errors. But my resolution is not 1920x1080.
what do i do? i also checked in the "hardware drivers" menu and it said my nvidia driver was in use and up to date.

---

### Post by Doc on 2010-09-30
Assuming you're using gnome go to System --> Administration --> Nvidia X Server settings and adjust to the resolution you desire.

I had a similar problem with a recent kernel update breaking the nvidia-kernel module but seems fixed after the above steps.

---

