---
title: "Unused program in the System Monitor."
date: 2011-02-11
forum: General Help
---

### Post by PowerWCRulez on 2011-02-11
Hello,

I wondering does the evolution-alarm-notify and evolution-data-server-1.4 would remove from the system monitor or just leave them alone. I didn't want to touch them that would cause system diseaster, can you please confirm for both if say yes to remove that will be good safe.. I am running older version of Ubuntu 5.10 on my lappy.

My firefox browser takes too much memory that runs very slowest and I need to cut down the both program list above or what I need to remove some other program in the system monitor. 

Thanks :)

---

### Post by Cheesehead on 2011-02-11
e-a-n is the appointment notifier. Evo's own alarm clock.

e-d-s is the address book, appointment list, and task list. It's  meant to be central databases used by other applications...for example, empathy should be able to save/retrieve contact info from e-d-s. Last time I checked it didn't, but the functionality is there at the Evo end.

Evo expects those processes to be running, so it may crash or bork Evo durong your session. (Might just respawn the processes, too)

---

