---
title: "NVIDIA driver problems"
date: 2012-01-25
forum: General Help
---

### Post by mkstallings1 on 2012-01-25
I just installed a proptrietary NVIDIA graphics driver and when I rebooted I can't even get GRUB or even a blinking curser..  All my screen says is "Input Not Support."  PLEASE HELP!

---

### Post by Cardale on 2012-01-25
Have you tried the recovery mode?

---

### Post by mkstallings1 on 2012-01-25
I don't get anything when I boot. No GRUB only option to go into BIOS.  I have a live CD up and runnin.  Can I do something from there?

---

### Post by mkstallings1 on 2012-01-25
I just realized I can't get into BIOS either.  I can only tell the computer what device to boot from.

---

### Post by mkstallings1 on 2012-01-26
OK, I went ahead and reinstalled Ubuntu and still the same problem.  When I boot, I get to the screen where I can either hit "escape" and get into BIOS or hit "F12" and select what media I want to boot from.  If I try to get into BIOS, it tries for about a second and then the screen goes blank with "Input Not Support" floating across the screen.  If I let it boot from the hdd, I get the same thing.  I am dual booting Windows 7 and Ubuntu 11.10 now.  It is a 64 bit system if that helps.  The computer itself is an e-machine.

---

### Post by mkstallings1 on 2012-01-26
Has anyone ever had this problem?

---

### Post by kooldino on 2012-01-26
Sure it's not a hardware issue?  I don't think GRUB uses your Nvidia driver...just a generic universal if anything.

---

### Post by mkstallings1 on 2012-01-26
I just think it must be a driver problem because it happened after I activated the NVIDIA driver.  Also, I can boot with a live cd just fine.

---

### Post by Tk007LwZFJW5ej on 2012-01-26
Did you try asking on the NVIDIA Linux forums, as it says here?

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by mkstallings1 on 2012-01-26
Thanks,I'll try that.

---

### Post by mkstallings1 on 2012-01-27
Alright, it looks like the problem is that GRUB is just not displaying.  If I wait or arrow down to what I think is the entry for what OS I want to boot into I can.  I used that to go into my Ubuntu 11.10 and change the graphics driver and everything but GRUB is now displaying just fine.  I think I'll try installing startup manager and see if I can tweak the resolution of GRUB and see what happens.

---

### Post by mkstallings1 on 2012-01-28
That's what it took.  I installed Startup Manager, tweaked the GRUB resolution, and now everything is fine.

---

### Post by Tk007LwZFJW5ej on 2012-01-29
What did you change it to/from and what was your actual screen res? I'm having a similar issue.

---

### Post by mkstallings1 on 2012-01-30
I don't think it really mattered what I changed it to. I think is was just me running startup manager because when I opened it, the resolution was set at 640x480.  I changed it to something higher and rebooted.  Now I could see GRUB, but I didn't like how it looked so I changed it back to 640x480.  Everything is now normal.  Hope that helps.

---

