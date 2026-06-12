---
title: "Grub default monitor"
date: 2010-09-27
forum: General Help
---

### Post by |utnubu| on 2010-09-27
Hello, I have an odd problem.
I have Ubuntu Lucid running on this computer with 2 graphics adapters and 3 monitors. Device0 is a NVidia FX5500 and has Screen0 connected to it. Device 1 is a NVidia Ti4200 with Screen1 and Screen2 connected. Screen0 sits between Screen1 & Screen2. I am using Xinerama with the nvidia drivers and I have gotten everything working ok with a few exceptions:

1) I was having trouble with blank TTYs(1-6), they would respond to commands but not display anything, I then rebooted and changed the default BIOS video adapter from the FX5500 to the Ti4200 and now have responsive TTYs but they are displayed on Screens 1&2 rather than Screen0. Is there a setting somewhere that says which display adapter to use for the TTYs? I want to be able to switch the default BIOS adapter back to the FX5500 so the default display is my middle monitor (Screen0)

2) I don't seem to see any boot info on startup - in previous version I saw details of everything as it starts up then a splash screen. This could be the same issue, the BIOS video adapter and the Grub video adapter not be set accordingly?

Thanks to anyone who can help, this is doing my head in :confused:

---

