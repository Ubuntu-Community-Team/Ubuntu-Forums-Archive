---
title: "Virtualbox broke"
date: 2009-08-11
forum: General Help
---

### Post by sp00ner on 2009-08-11
My system had been running great for weeks until tonight. I wanted to install Windows 7 on a VM on my Ubuntu laptop. So I installed Virtualbox. The install prompted for a reboot so I did. When I rebooted, GNOME prompted for username and password. Once I entered them, all it would come up to is a blank desktop =( So after some muddling around I managed to find the "safe mode" style boot-up. Was then givin a choice to do an X repair which I did. So now I can get back into to GNOME but now my wireless card and sound drivers dont work. I dont know how to install these drivers back because they were all setup automatically during setup. Can I initiate some sort of hardware detection that will install back the missing drivers?

---

### Post by razorboy5 on 2009-08-11
how does the wireless and sound card "not work" there can be many problems a little more detail may be necessary and/or helpful

as for wireless try running alt+f2 then type in the box nm-applet

---

### Post by sp00ner on 2009-08-12
The hardware is still recognized but they just dont work. For example, on the network applet I used to be able to right click it and there would be a selection to enable wireless. That is no longer there. I can connect via eth0 wired connection but support for wireless is gone. As for the sound card, the speaker icon is still there in my taskbar but it has a red x in it and it says there is no device to control when I click on it. the nm-applet command just loaded a second network icon on the taskbar.

---

### Post by sp00ner on 2009-08-12
Bump

---

### Post by sp00ner on 2009-08-12
My system had been running great for weeks until tonight. I wanted to install Windows 7 on a VM on my Ubuntu laptop. So I installed Virtualbox. The install prompted for a reboot so I did. When I rebooted, GNOME prompted for username and password. Once I entered them, all it would come up to is a blank desktop =( So after some muddling around I managed to find the "safe mode" style boot-up. Was then givin a choice to do an X repair which I did. So now I can get back into to GNOME but now my wireless card and sound drivers dont work. For example, the wireless card hardware is still being recognized by doing a lspci but the network manager applet no longer has support for my wireless networks. For the sound card, its the same situation. The hardware is recognized but the speaker icon has a red x and if I click on it, it says there is no device to control. I'm thinking the modules for these devices are not loading anymore but I dont know the name of them. These devices were both detected and supported when I first installed Ubuntu.

---

### Post by overdrank on 2009-08-12
Threads merged.

---

### Post by sp00ner on 2009-08-12
I have some more details on this issue. If I hit escape and choose to run the kernel 2.6.24-24 - generic all hardware works fine, if I choose kernel 2.6.24-24 386 (or just let it boot normally), the sound and wireless wont work. I compared the results from doing a lsmod on both kernel bootups. It looks like there are quite few modules missing from the 386 bootup. iwl3945 is what I beleive I need for the wireless card and there is a bunch of modules that start with snd that are missing, snd_hda_intel being the one that sounds most important. Question is how do I get these modules back into the 386 bootup or do I just use the generic bootup from now since everything seems to work with it?

---

