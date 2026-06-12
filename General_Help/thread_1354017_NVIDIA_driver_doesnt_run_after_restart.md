---
title: "NVIDIA driver doesnt run after restart"
date: 2009-12-13
forum: General Help
---

### Post by eival on 2009-12-13
i manually installed the latest drivers a few weeks ago but i haven't had to restart my computer since till today an when i did the drivers didnt load, i got the "ubuntu is running in low graphics mode" message.

during the bootup after the ubuntu load bar finished, the command line appeared showing several checks and at the bottom it had something about a script and the screen would go black, an then reappear on the same line about 3 times.

reinstalling the drivers takes me out of low graphics mode, but if i restart i get the same issue again.

im using Ubuntu 8.04

---

### Post by fragos on 2009-12-13
I recommend you install drivers with Synaptic. They have been compiled to work with kernel you're using. When you install manually the package manager won't know to upgrade the Nvidia driver when a kernel update is installed. Newer Ubuntu versions like 9.10 provide a Hardware Driver preferences to make this process simpler. In that case you'll be told which drivers are available and which is recommended.

---

### Post by eival on 2009-12-13
the driver in synaptic is old as hell.

so back to my issue at hand.

how do i fix the issue of ubuntu going into low graphics mode whenever i restart?

thank you.

---

### Post by Physical Hook on 2009-12-13
[LIST=1]
[*]Which NVidia driver you are trying to install and what is the model of your video card ?
[*].. X.org version ?
[*].. kernel version ?
[/LIST]

---

### Post by eival on 2009-12-14
> **Physical Hook said:**
> [LIST=1]
[*]Which NVidia driver you are trying to install and what is the model of your video card ?
[*].. X.org version ?
[*].. kernel version ?
[/LIST]

im not trying, its already installed successfully, but my specs are

driver 190.42 for GeForce Go 6150

11.0 - X.org

i always use the latest kernal update

---

