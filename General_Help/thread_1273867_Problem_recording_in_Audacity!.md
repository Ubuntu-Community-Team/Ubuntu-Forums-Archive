---
title: "Problem recording in Audacity!"
date: 2009-09-23
forum: General Help
---

### Post by Naitogunjin on 2009-09-23
Hello everyone,
I have a DigiTech RP 150 Modeling Guitar Processor, and i have connected it to my computer through usb. Im trying to record straight through that onto audacity. I got it to where it will record sometimes but it only lets me record once. In other words if i record then stop then try and record again i get an error message. The error message says:

[COLOR=Red]Error while opening sound device. Please check the input device settings and the project sample rate. [/COLOR]:confused:

I have tried different Project Rates and nothing is working. If anybody has had this problem before or knows how to fix it please let me know. 

My O.S. is Ubuntu 9.04 and im using the version 1.3.7 (Unicode) of Audacity.
Thanks

---

### Post by tkoco on 2009-09-23
Sounds like you have multiple sound devices. ```
aplay -l
```and see how many sound devices are listed. 
Given this list by the aplay command, make sure "audacity" devices are correctly configured. The other "gotcha" (with multiple sound devices) to watchout for is the correct assignment of sound devices. Audacity does not like sound cards swapping places in the order of assignment. Look at the "/etc/modprobe.d/alsa-base.conf" file for sound card assignments.

> **Naitogunjin said:**
> Hello everyone,
I have a DigiTech RP 150 Modeling Guitar Processor, and i have connected it to my computer through usb. Im trying to record straight through that onto audacity. I got it to where it will record sometimes but it only lets me record once. In other words if i record then stop then try and record again i get an error message. The error message says:

[COLOR=Red]Error while opening sound device. Please check the input device settings and the project sample rate. [/COLOR]:confused:

I have tried different Project Rates and nothing is working. If anybody has had this problem before or knows how to fix it please let me know. 

My O.S. is Ubuntu 9.04 and im using the version 1.3.7 (Unicode) of Audacity.
Thanks

---

