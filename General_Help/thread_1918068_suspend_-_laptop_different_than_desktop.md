---
title: "suspend - laptop different than desktop"
date: 2012-01-31
forum: General Help
---

### Post by missmoondog on 2012-01-31
why does a laptop coming out of suspend mode load my xubuntu os immediately where as my desktops load the option to choose which os to boot?

is there a way to change that on any of these machine?

thank you

---

### Post by Jose Catre-Vandis on 2012-01-31
Sounds like the desktop is not suspending but shutting down.

Check bios for Sleep modes (you probably want S3)

---

### Post by missmoondog on 2012-02-01
if the desktops are shutting down, why does the light still blink on the front of computer, as if sleeping, and unless the unbuntu install edited my bios for me, the bios power option is set for s3.

thank you

---

### Post by Jose Catre-Vandis on 2012-02-04
You have four likely options:

Sleep (most power usage)
Hybrid Sleep (somewhere between sleep and hibernate but should return you to the dekstop immediately)
Hibernate (saves desktop to file and shuts down, but resumes desktop on startup)
Shutdown ;)

PCs and laptops will have different hardware / bios approaches, so you may need to fiddle with the settings to get your desired effect.

---

### Post by missmoondog on 2012-02-06
thank you.

just seems peculiar that 3 desktops, all different models will boot straight into OS, but all 4 laptops, different models also, boot to the option of chosing OS.

always thought hibernate was useless and is usually totally disabled under windows. simply never bothered to look into disabling it in linux.

---

