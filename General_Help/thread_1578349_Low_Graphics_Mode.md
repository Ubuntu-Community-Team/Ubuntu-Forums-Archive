---
title: "Low Graphics Mode"
date: 2010-09-20
forum: General Help
---

### Post by FahadMKS on 2010-09-20
I do not know what exactly has happened to my computer.

I have a computer with the Ubuntu installed and I have also installed the Nvidia Recommended graphics drivers and had updated my Ubuntu.
Now the issue is that , I get a prompt as Ubuntu is running in low graphics mode and I need to reconfigure the X server.
When I select the option as to restart the X server, the issue gets resolved just for that session and then next time I login, I get the same error message again.

What should I do to get rid of this issue?
Please do help me, any help will be appreciated.

---

### Post by 3Miro on 2010-09-20
Got to System -> Admin -> Hardware Drivers. Remove the proprietary Nvidia driver, then reboot. Afterwards, install the driver again and reboot again.

This is a very Windows like solution, but it should work. There is a way to fix that manually, but is usually too much hassle.

---

### Post by FahadMKS on 2010-09-20
If you are sure about this, I will give a try, but I do only have a limited Internet usage, so maybe I will try tomorrow early morning and will let you know.

---

### Post by 3Miro on 2010-09-20
> **FahadMKS said:**
> If you are sure about this, I will give a try, but I do only have a limited Internet usage, so maybe I will try tomorrow early morning and will let you know.

What you are describing usually happens if the Nvidia kernel module failed to compile. For every Kernel that you have installed, you need a separate Nvidia module. Most modules come with the kernel itself, however, due to legality the Nvidia one cannot be included by default. What the kernel is updated, a new module should be compiled, however, if this fails, then you will be unable to use the graphics driver. There is a way to manually recompile the kernel module, but I am not sure how. I just reinstall the driver and it has always worked for me in the past.

---

### Post by FahadMKS on 2010-09-21
Yes, now the issue has been resolved on reinstalling the Nvidia Drivers.

Thank you guys.

---

