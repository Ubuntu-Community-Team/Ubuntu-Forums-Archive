---
title: "Dual monitors not working"
date: 2012-04-29
forum: General Help
---

### Post by Th3Alchemist on 2012-04-29
I recently installed Ubuntu 12.04 (64bits) in my laptop, and I can't get an external monitor (dual monitors) working.

I installed with success the latest NVIDIA driver but still no success.

On the Displays option when I click on "Detect Displays", nothing happens either.

```

marcsoler@R510:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)

```

---

### Post by keithpeter on 2012-04-29
Hello Th3Alchemist

Are you using the nvidia restricted drivers (usually installed via jockey)?

If so do you have the nvidia-settings app (minty green icon) installed? 

I use that to set up twinview. 

I'm using a GT520 card with two outputs, one dvi and one vga on a desktop PC. See a screen grab of nvidia-settings below (actually on debian wheezy but its the same on Ubuntu)

The Display app within Ubuntu just sees both screens as one big one.

---

### Post by Th3Alchemist on 2012-04-29
Thank you **keithpeter** found it and it is working!

Thanks!

---

### Post by keithpeter on 2012-04-29
> **Th3Alchemist said:**
> Thank you **keithpeter** found it and it is working!

Thanks!

Great!

[http://ubuntuforums.org/showthread.php?t=1967803](http://ubuntuforums.org/showthread.php?t=1967803)

The other way of enabling both monitors is to use a separate X server for each monitor, that is an option in the dropdown list in the nvidia-settings app.

Apparently, there is an issue with that second option. I've found the monitor with the dvi cable just shows the white screen with the black cross same as on the thread above.

I'm sticking to twinview for a bit...

Can you click on Thread Tools and mark this thread as solved?

---

