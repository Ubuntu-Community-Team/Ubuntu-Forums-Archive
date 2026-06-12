---
title: "Virtualbox 3.1.2, Karmic amd64 and memory usage"
date: 2010-02-03
forum: General Help
---

### Post by gaming_guy on 2010-02-03
I've recently installed ubuntu karmic amd64 on my system (after doing a fresh install from 8.10 amd64) and noticed that the memory usage when using virtualbox (the 64bit version & not the OSE version) goes from just under 1gb after booting up karmic (the host) to around 97% - 99% of my 4gb ram when i've only allocated 512mb ram for the guest OS.

I can understand that VM's are quite intensive, but this never used to happen under 8.10 where i struggled to hit 3gb even with 2 VMs running. I also know that VBox itself needs ram to run but 2gb to run VBox seems rather excessive to me when the guest only has 512mb allocated.

Is there anything that i can do to reduce the memory usage as it concerns me that VBox uses just over 2gb ram when i only allocated 512mb to the guest?

Edit - please feel free to move this post as i wasn't sure if i should post it in here (general) or the virtalization board

---

### Post by howefield on 2010-02-04
[QUOTE=gaming_guy;8767808]...noticed that the memory usage when using virtualbox (the 64bit version & not the OSE version) goes from just under 1gb after booting up karmic (the host) to around 97% - 99% of my 4gb ram when i've only allocated 512mb ram for the guest OS.

You haven't said anything to prove virtualbox is at fault.

Open a terminal and type

```
top
```

Is it showing virtualbox as the culprit ?

---

### Post by gaming_guy on 2010-02-04
Thanks for the reply, howefield :)

VBox was using the most memory (15%+) when top was run.

i think i might have found out why the memory usage was so high - i had just installed Debian as a guest and after finshing the install it never freed the memory on the host until i rebooted the host. After rebooting the memory usage of the host seemed to go back to more reasonable amounts even with the VM running.

---

