---
title: "Ubuntu Live CD does not boot"
date: 2010-09-20
forum: General Help
---

### Post by rodrigian on 2010-09-20
I recently downloaded Ubuntu 10.04.1

The thing is that as i have a VAIO notebook with Nvidia GeForce 310M graphics,  the Nouveau driver does not recongize it and so it gives me a black  screen (Actually it's more as if the display is off)

The thing is that I think that if I disable Plymounth, the computer should boot normally.

What I want to do, and please help me with this is

- Disable plymounth

- Boot the desktop

- Install Nvidia propietary drivers

- Enable PLyomounth

Thanks in advance. If you have another solution please let me know.

---

### Post by TheNessus on 2010-09-20
> **rodrigian said:**
> I recently downloaded Ubuntu 10.04.1

The thing is that as i have a VAIO notebook with Nvidia GeForce 310M graphics,  the Nouveau driver does not recongize it and so it gives me a black  screen (Actually it's more as if the display is off)

The thing is that I think that if I disable Plymounth, the computer should boot normally.

What I want to do, and please help me with this is

- Disable plymounth

- Boot the desktop

- Install Nvidia propietary drivers

- Enable PLyomounth

Thanks in advance. If you have another solution please let me know.
Hi.

You can load the live cd with the nomodeset option, this will prevent using the open source graphics driver and use no effects. no trouble should arise then. Then when after installation, load in safe graphics mode and select root shell with networking. Then you can easily install the latest propriety driver use "sudo apt-get install nvidia-current". After doing "sudo apt-get update" of course.
reboot. if you have trouble after that come back here.

---

### Post by rodrigian on 2010-09-21
Thanks, it worked perfectly

---

