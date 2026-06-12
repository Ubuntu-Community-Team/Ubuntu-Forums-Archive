---
title: "Virtual Machine + Good graphics"
date: 2011-03-26
forum: General Help
---

### Post by Julian Luna on 2011-03-26
How to accelerate the graphics by hardware on a virtual machine with XP if it didn't respond with the setting's options: enable 3D acceleracion and enable 2D video acceleration? How to path it to my video card?

---

### Post by Vaphell on 2011-03-27
virtualbox? do you have vb addons installed? either way personally i've seen acceleration working only once, with nvidia card. Radeon never worked for me.

---

### Post by coldraven on 2011-03-27
I don't think what you want is possible. The guest OS is being shown virtual hardware.

---

### Post by Vaphell on 2011-03-27
yes, but that virtual hardware passes calls to the host. The only problem is that it fails more often than not, for example on my box google earth in guest runs but is full of weird lines and flickers like mad.

---

