---
title: "Unable to set cpu frequency"
date: 2011-01-03
forum: General Help
---

### Post by sarin_cv on 2011-01-03
Hi,

I'm having a Dell Studio 1535 laptop with Intel Dual core 2.10 GHz processor. I've added the CPU scaling monitor to the panel. I'm able to set the frequency or the governor from that applet when in battery mode. But when AC is plugged in, I'm not able to change it. The default value is the lowest available frequency(1.2 GHz per core) in AC. 

I've tried installing granola also but it's behavior is also the same.

Any help is greatly appreciated as the performance gets affected when connected directly. 
Thanks,
sarin

---

### Post by dcstar on 2011-01-04
> **sarin_cv said:**
> Hi,

I'm having a Dell Studio 1535 laptop with Intel Dual core 2.10 GHz processor. I've added the CPU scaling monitor to the panel. I'm able to set the frequency or the governor from that applet when in battery mode. But when AC is plugged in, I'm not able to change it. The default value is the lowest available frequency(1.2 GHz per core) in AC. 

I've tried installing granola also but it's behavior is also the same.

Any help is greatly appreciated as the performance gets affected when connected directly. 
Thanks,
sarin

Check that the BIOS settings allow changes.

---

### Post by sarin_cv on 2011-01-04
k...will try it...

---

### Post by sarin_cv on 2011-01-04
couldn't find anything related to scaling in BIOS except the speedstep. It is already enabled and when I turned it off, on bootup ubuntu shows frequency scaling unsupported...so I assume that it should be enabled...

---

### Post by dcstar on 2011-01-05
> **sarin_cv said:**
> couldn't find anything related to scaling in BIOS except the speedstep. It is already enabled and when I turned it off, on bootup ubuntu shows frequency scaling unsupported...so I assume that it should be enabled...

Try installing the **powernowd** package.

---

