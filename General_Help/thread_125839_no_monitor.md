---
title: "no monitor"
date: 2006-02-05
forum: General Help
---

### Post by bountonw on 2006-02-05
I have just installed ubuntu onto one of my computers for the first time.  (I am hoping to migrate my entire office.)  Unfortunately, after installation, none of my monitors works with the linux installed computer.  

One of the monitors said, 

"Out of frequency
HF 90.1 kHz
VF 60.0 HZ
Operation Frequency
HF 30-71 kHz
vF 50-160 Hz"

When I tried plugging in a different monitor, I had a similar message.

Now that I have no monitors that work, I don't know what to do as I can't see the screen.  I have not logged in for the first time.  I could see progress and enter in the scecifications, until the final re-boot.  Now it is a very dark world.  What do I do now?  The computer is on.  I don't even know how to shut down as I can't see the first screen which I assume is my log-in screen.  I don't mind trying to operate in the dark if I have very clear instructions on how to turn the lights back on.

---

### Post by mustang on 2006-02-05
If you're dual booting and using the GRUB manager, you can select the recovery mode and then

```
sudo dpkg-reconfigure xserver-xorg
```

If not, you could boot off the Ubuntu install CD and then look for recovery mode there and then do run the code I gave above.

When you're configuring the xserver, I reccommend using its own default values and then changing them later on. When it gets to the monitor portion, it'll autodetect a viewable refresh rate. If you are not satisfied, you can still change it by modifying /etc/X11/xorg.conf

---

### Post by bountonw on 2006-02-05
Thank you.  Rebooting from the CD seemed to solve the problem.

---

