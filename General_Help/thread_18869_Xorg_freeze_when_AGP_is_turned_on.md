---
title: "Xorg freeze when AGP is turned on"
date: 2005-03-09
forum: General Help
---

### Post by d98_ama on 2005-03-09
Hi,

I have a problem with my Ubuntu install. I'm using the video drivers from Nvidia, but when I turn on AGP (NvAgp set to 1, 2 or 3) and start GDM the screen just turns black and I can't do anything.
The only way to get out of this is to reboot my computer (with the reset button, Ctrl+Alt+del doesn't work).

It is possible to SSH to access the box when it is in the frozen state. When I do that I can see that Xorg takes 100% cpu, but I can't find anything strange in the X logs or with dmesg.
Also, it is not possible to kill Xorg. Not even with kill -9.

Anyone has any idea why it behaves like this?

/Anders

---

### Post by alastair on 2005-03-09
I cannot help here - but just to say that a friend's machine at my work (GeForce 6600, FC2, Dell) also doesn't work with AGP on. Neither Linux AGP, or NVidia AGP - we turn AGP off in the X config file and the machine seems happy. Symptoms were - it locked up after a few minutes in X.

I tried a few different kernels, custom compiled, different NVidia driver version ... no luck.

Luckily, he seems happy enough and can still do his work.

---

### Post by iotc247 on 2005-03-11
[QUOTE=alastair]I cannot help here - but just to say that a friend's machine at my work (GeForce 6600, FC2, Dell) also doesn't work with AGP on. Neither Linux AGP, or NVidia AGP - we turn AGP off in the X config file and the machine seems happy. Symptoms were - it locked up after a few minutes in X.

I tried a few different kernels, custom compiled, different NVidia driver version ... no luck.

Luckily, he seems happy enough and can still do his work.[/QUOTE]
 Yeah mine doesnt either... NvAGP doesnt support sis 760 so thats out and agpgart makes xorg freeze.... Well see if the new drivers help... (nvidia)

---

