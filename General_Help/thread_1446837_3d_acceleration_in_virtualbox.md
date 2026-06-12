---
title: "3d acceleration in virtualbox"
date: 2010-04-04
forum: General Help
---

### Post by camaron1 on 2010-04-04
I use Windows 7 with Virtualbox in Ubuntu 9.10. The guest additions are installed but I don't get 3d acceleration (no aereo theme). I thought that was due to my graphic card (GeForce 7050) but I've just installed  Ubuntu 10.4 with Virtualbox and does have 3d acceleration. Any ideas?

---

### Post by Silent Warrior on 2010-04-04
Hm... Isn't there a menu-item for installing WineD3D, in the VM's menubar? How much graphics-memory have you given it?

---

### Post by camaron1 on 2010-04-04
> **Silent Warrior said:**
> Hm... Isn't there a menu-item for installing WineD3D, in the VM's menubar? How much graphics-memory have you given it?

I use Virtualbox no VM. I don't have that item in my menu. I gave it 125 MB

Thanks

---

### Post by camaron1 on 2010-04-05
bump!

---

### Post by sikander3786 on 2010-04-05
> **camaron1 said:**
> I use Windows 7 with Virtualbox in Ubuntu 9.10. The guest additions are installed but I don't get 3d acceleration (no aereo theme). I thought that was due to my graphic card (GeForce 7050) but I've just installed  Ubuntu 10.4 with Virtualbox and does have 3d acceleration. Any ideas?

Hi.

In the device manger of Win 7 check if the Virtualbox Graphics Adapter is installed correctly.

Just a thought. On the machine settings menu, is the 3d acceleration enabled?

---

### Post by camaron1 on 2010-04-05
```
Hi.

In the device manger of Win 7 check if the Virtualbox Graphics Adapter  is installed correctly.

Just a thought. On the machine settings menu, is the 3d acceleration  enabled
```

Hi, Yes 3d is enabled in the settings but I will check Win 7 settings when I get home tonight. 
Thanks

---

### Post by NightwishFan on 2010-04-05
You need to enable guest additions in virtualbox. To enable the 3d acceleration in Windows7, **you need to boot it in safe mode** and then run the installer exe. You can boot it in safe mode by holding f8 while booting.
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

---

### Post by camaron1 on 2010-04-05
> **NightwishFan said:**
> You need to enable guest additions in virtualbox. To enable the 3d acceleration in Windows7, **you need to boot it in safe mode** and then run the installer exe. You can boot it in safe mode by holding f8 while booting.
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

That is exactly what it is: I had come across that information too. Here is the problem: I can't access the virtual BIOS. Pressing f8 does nothing (I guess because the guest additions are not active while the system is booting so the keyboard for the virtual machine is not active , I don't know). Would you be able to tell me how to get round this issue? Help greatly appreciated.

---

### Post by NightwishFan on 2010-04-05
Keep tapping f8 right after you click to load the virtual machine (ensure the virtual windows7 is the active window) until it goes into safe mode. It is not a bios you need but the normal Windows advanced boot menu. I only remember the f8 trick I am unsure if it was changed by Windows7, but I doubt it.

---

### Post by camaron1 on 2010-04-05
> **NightwishFan said:**
> Keep tapping f8 right after you click to load the virtual machine (ensure the virtual windows7 is the active window) until it goes into safe mode. It is not a bios you need but the normal Windows advanced boot menu. I only remember the f8 trick I am unsure if it was changed by Windows7, but I doubt it.
Sure I've tried this many times, believing that if 20 taps  didn't do then let's go for 30. I'm afraid it doesn't work.

---

### Post by NightwishFan on 2010-04-05
It works here on WindowsXp. Not sure what to tell you. Check if there is alternate ways to get into safe mode. I will get back to you.
[http://www.bleepingcomputer.com/tutorials/tutorial61.html#windows7](http://www.bleepingcomputer.com/tutorials/tutorial61.html#windows7)
[http://www.bleepingcomputer.com/tutorials/tutorial61.html#force_safemode](http://www.bleepingcomputer.com/tutorials/tutorial61.html#force_safemode)

---

### Post by camaron1 on 2010-04-05
> **NightwishFan said:**
> It works here on WindowsXp. Not sure what to tell you. Check if there is alternate ways to get into safe mode. I will get back to you.
[http://www.bleepingcomputer.com/tutorials/tutorial61.html#windows7](http://www.bleepingcomputer.com/tutorials/tutorial61.html#windows7)
[http://www.bleepingcomputer.com/tutorials/tutorial61.html#force_safemode](http://www.bleepingcomputer.com/tutorials/tutorial61.html#force_safemode)

Thanks for that. I'll see what I can do myself when I get back home tonight

---

### Post by NightwishFan on 2010-04-05
Good luck, I hope you get it working.

---

### Post by camaron1 on 2010-04-06
I managed to boot into Windows in safe mode and reinstalled guest additions with no joy.
Oh well..

---

