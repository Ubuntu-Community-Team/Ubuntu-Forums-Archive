---
title: "dell inspiron 600m shutdown problem"
date: 2010-09-27
forum: General Help
---

### Post by cadogan281 on 2010-09-27
i just installed ubuntu 10.04 and everything seems to be working fine except when i try to restart or shutdown the computer.when i do shutdown it logs out but never shuts off the laptop.is this a known problem for this model dell?

---

### Post by harrismh777 on 2010-09-27
This is a known problem on lots of hardware models. 

Sometimes my HP slimline will not power-off, although it "usually" does.

Make sure your bios settings are correct. Have you dissabled the auto-power stuff....?

The most important thing is that the OS is shutting down (unmounting partitions, etc) and that the machine is in a state where you can power off.

Just hold the power button in on the laptop until it powers off...AFTER you shutdown the OS.

---

### Post by cadogan281 on 2010-09-27
i was wanting to make sure it wouldnt hurt the laptop or filesystem by shutting it down like that.once i hit the shutdown button,it goes to the gnome login screen and i can hold down the power button to shut it down.does anyone know if there is a possilbe fix for that in 10.10?where were the options for the auto-power?

---

### Post by harrismh777 on 2010-09-27
> **cadogan281 said:**
> i was wanting to make sure it wouldnt hurt the laptop or filesystem by shutting it down like that.once i hit the shutdown button,it goes to the gnome login screen and i can hold down the power button to shut it down.does anyone know if there is a possilbe fix for that in 10.10?where were the options for the auto-power?

No no no. This is a whole nuther matter !

You can configure your machine to do different things when the power button is pressed. In your case it is JUST logging off. DO NOT TURN IT OFF FROM THERE !

You can configure the power button to shutdown the OS and then power off, if the auto-power stuff is configured correctly. 

Having said that, normally should happen is that you will click the power icon on your gnome desktop tool bar and select "shutdown". Wait for the OS to shutdown, which may leave the hardware "powered" on. THEN press the power button and hold it for five seconds for final power down.

Some folks have their power button configured for suspend, or hibernate. This is just a matter of personal preference. 

The main thing to remember is that the OS needs to be shutdown correctly so that the drives unmount cleanly. That has NOT occurred if you are sitting at a gnome login panel. 


:popcorn:

---

