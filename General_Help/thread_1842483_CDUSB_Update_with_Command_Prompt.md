---
title: "CD/USB Update with Command Prompt"
date: 2011-09-11
forum: General Help
---

### Post by Jockboy98295 on 2011-09-11
Hey guys. I need a little help here. trying to update my desktop to 11.04 from lucid. However, i only have the command prompt. I had to replace my motherboard and CPU, in the process I no longer have a graphics card. So now I dont have a GUI. Wondering if there is a way to upgrade from a CD or USB while using the command prompt. Ill worry about the GUI later. :) Thanks guys.Also dont have a direct connection to the internet, using a wireless connection only, so dont have internet. Which is why I need to update via a CD or USB.

---

### Post by dcstar on 2011-09-12
> **Jockboy98295 said:**
> Hey guys. I need a little help here. trying to update my desktop to 11.04 from lucid. However, i only have the command prompt. I had to replace my motherboard and CPU, in the process I no longer have a graphics card. So now I dont have a GUI. Wondering if there is a way to upgrade from a CD or USB while using the command prompt. Ill worry about the GUI later. :) Thanks guys.Also dont have a direct connection to the internet, using a wireless connection only, so dont have internet. Which is why I need to update via a CD or USB.

Boot from a Live CD/USB, mount the hard drive and rename the /etc/X11/xorg.conf file.

Then reboot the system and your GUI should be back.

---

