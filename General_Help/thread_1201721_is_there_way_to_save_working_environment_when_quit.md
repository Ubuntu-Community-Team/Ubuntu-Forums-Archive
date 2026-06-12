---
title: "is there way to save working environment when quit ubuntu"
date: 2009-07-01
forum: General Help
---

### Post by bsmile on 2009-07-01
just like hibernation, but writing all the information onto the hard disk thus even if I reboot to ubuntu, I can easily continue with my work. Hibernation itself does not meet my need for two reasons, one is that it needs the machine to always have power on, second is that I cannot leave ubuntu and then come back ...

---

### Post by mikewhatever on 2009-07-01
Try System->Preferences->Startup Applications, the Options tab, and tick the 'Remember the running apps' box.

I think you confuse Hibernation with Suspense to RAM. Hibernation does not require that the machined remains powered. Data is copied from RAM to disk and the computer turns off.

---

### Post by doas777 on 2009-07-01
> **mikewhatever said:**
> Try System->Preferences->Startup Applications, the Options tab, and tick the 'Remember the running apps' box.

I think you confuse Hibernation with Suspense to RAM. Hibernation does not require that the machined remains powered. Data is copied from RAM to disk and the computer turns off.

I've had nothing but trouble with that feature. perhaps it will work better for you than i. I often found it launching things that i have set as startup applications twice, once by the session startup, and one from app memory.

---

### Post by bsmile on 2009-07-02
> **mikewhatever said:**
> Try System->Preferences->Startup Applications, the Options tab, and tick the 'Remember the running apps' box.

I think you confuse Hibernation with Suspense to RAM. Hibernation does not require that the machined remains powered. Data is copied from RAM to disk and the computer turns off.

Thanks, I guess I had some confusion too, but why would hibernation still consumes battery power then? If in hibernation, why would battery support say 40-50 days, instead of forever?

---

### Post by Th3_uN1Qu3 on 2009-07-02
Because the battery **discharges by itself over time.** But even if the battery goes to zero your laptop will still be able to resume from hibernation as all data is on the hard disk. (that if after waking up it does not freeze at the login screen like mine does)

---

### Post by darthmob on 2009-07-02
hibernation aka suspend to disk: all information about running programs is written to the hard disk - no power is required.

suspend aka suspend to ram: all information is kept in ram. the ram is non-permanent memory so you need a minimum of power to keep it active.

---

### Post by bsmile on 2009-07-02
To be precise, my question is how to back up what I left with linux when I power off or restart to windows. I hope when I restart back to ubuntu, what is on the screen is what I left unfinished last time. 

Hibernation only helps when I want to save battery, but it does NOT help quitting linux. In principle, the power still supports the least booting information saved in the registers(I guess), thus if one powers off the computer, it would give you a clean start up, instead of picking up what was left last time.

Please help, any recommendation is appreciated! If this feature cannot be realized in the current ubuntu, can it be added in the newer release of ubuntu cause I think this is a great feature to have ...

---

### Post by bsmile on 2009-07-06
Please help!!

---

### Post by bsmile on 2009-07-24
> **mikewhatever said:**
> Try System->Preferences->Startup Applications, the Options tab, and tick the 'Remember the running apps' box.

I think you confuse Hibernation with Suspense to RAM. Hibernation does not require that the machined remains powered. Data is copied from RAM to disk and the computer turns off.

Thanks! Just a comment, There is one more layer to bypass, 

System->Preferences->Session->Startup Applications, the Options tab

BTW, how can I see whether two applications are started twice?

---

