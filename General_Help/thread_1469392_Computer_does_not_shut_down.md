---
title: "Computer does not shut down"
date: 2010-05-02
forum: General Help
---

### Post by aivan on 2010-05-02
Hi all,

Since a long time I have a problem when shutting down my computer. 

Here are the symptoms:
After pressing "shutdown" (or issuing a command in terminal) it happens (always) that the screen is still working at the end of shutdown process (ubuntu progress bar is at minimum and it stays visible). Also, CPU fan is still working. However, power and HDD lights go off.

The only possible way to shutdown computer at that moment is holding power button for 5 seconds.

However, restart works OK.

Now, I am sure that shutdown worked earlier fine, but unfortunately I cannot remember when the problems started: either when I installed 8.04 or after installing some of the kernel updates.

Configuration is following:
Asus 5pgl-mx motherboard, 1.5 GB ram, nvidia graphic card (sorry, not sure what model), etc.

I have ubuntu 8.04 installed, and I do install regulary all the updates including new kernels, etc.

I have being searching for the solution for a long time, but none of the suggestions helper (some people solved the issue with acpi=force and similar kernel parameters, but none of them worked for me).

Does anyone has any idea how to solve the issue, since it is a bit (actually a lot) annoying?

Thanks in advance,
Ivan

---

### Post by dino99 on 2010-05-02
how are your bios settings about last state ?

even if acpi=force does not work , its something to dig around acpi, try to remove/purge it with synaptic then reinstall it, or reconfigure it 

should try with 

acpid, acpi-support, powermgmt-base

---

### Post by aivan on 2010-05-02
Hi, thanks for suggestions.

I have already tried playing around with BIOS settings (enabling/disabling ACPI 2.0 support, setting to default values, etc.) but with no luck.

Here is one more hint (just tried out):

- Starting with generic kernel, and going for option "normal boot (first option)" results with same problems (not shutting down), however

- Starting with generic kernel, and choosing "root prompt (last option)" results with "shutdown -h now" being able to shutdown computer properly.

:(

---

