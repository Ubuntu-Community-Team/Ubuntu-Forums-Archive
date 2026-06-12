---
title: "system does not shut down"
date: 2010-07-09
forum: General Help
---

### Post by mariosangiorgio on 2010-07-09
Hi,
I am experiencing an issue with the system shut down.
Everything works fine, but the system is not able to automatically power off and I have to manually switch it off.
How could I fix this behavior?

Thanks,
Mario

---

### Post by quimkaos on 2010-07-09
does it hangs wile powering off or it says something like "you can now turn off your computer"? because if it asks for turn off you probably have ACPI disabled in your BIOS.

---

### Post by mariosangiorgio on 2010-07-09
> **quimkaos said:**
> does it hangs wile powering off or it says something like "you can now turn off your computer"? because if it asks for turn off you probably have ACPI disabled in your BIOS.
It doesn't say anything :(

I don't think that ACPI is disabled because Windows it was able to power off the system.
Can you please tell me how can I check if Linux does or doesn't recognize ACPI?

---

### Post by quimkaos on 2010-07-09
then you probably have an application hanging when you try to reboot/shutdown. Is this going on since you install Xubuntu? Try looking at the logs if you can find any error message.

---

### Post by mariosangiorgio on 2010-07-09
> **quimkaos said:**
> then you probably have an application hanging when you try to reboot/shutdown. Is this going on since you install Xubuntu? Try looking at the logs if you can find any error message.
It always happened, I just installed Xubuntu and I didn't customized it at all :(
Where can I find the logs?

---

### Post by quimkaos on 2010-07-09
i use a tool that comes by default with Ubuntu and it is in system > administration... i don't know if xubuntu have one by default. anyway you can find your logs in /var/log...

Meanwhile i found this that can be helpful to you:
[http://ubuntuforums.org/showthread.php?t=657927](http://ubuntuforums.org/showthread.php?t=657927)

---

