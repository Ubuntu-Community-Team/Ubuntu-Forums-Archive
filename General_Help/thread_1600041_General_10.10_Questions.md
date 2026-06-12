---
title: "General 10.10 Questions"
date: 2010-10-18
forum: General Help
---

### Post by eraker on 2010-10-18
I haven't upgraded in awhile (was running 9.4), but I did a fresh install of 10.10 recently (i386 as no version of amd64 would work, livecd or otherwise) and it looks pretty good. 

Even so,I had a few quick questions that I haven't been able to find the answer to, so I thought I'd put them together here:

1. No more xorg.conf? Is there a file that holds the settings required for my display etc?
2. No more menu.lst? I wanted to disable the boot-up splash screen but I can't figure out how to do it. Any suggestions?

Thanks for any suggestions you can provide.

---

### Post by Frogs Hair on 2010-10-18
1. Preferences menu > monitors , if using Nvidia drivers see Nvidia  X Sever Settings or its ATI counterpart on the administration  menu.

---

### Post by efflandt on 2010-10-18
1. The xorg.conf file has not been used for awhile unless you specifically need one for something special (like special resolution not recognized automatically).  If you install proprietary video drivers [usually by activating them in System > Administration > Additional Drivers (or Hardware Drivers in earlier Ubuntu)] they usually provide a basic xorg.conf for that type of video.  Although, most settings can be made using the app that came with them, like Catalyst for ATI or NVIDIA X Server Settings for nVidia.

2. grub2 became the default grub since 9.10.  grub2 does not use menu.lst, it uses grub.cfg.  But you are NOT supposed to edit that directly because it gets overwritten when anything does update-grub (kernel updates, etc.).  So any customization should be done by editing /etc/default/grub or scripts in /etc/grub.d/.

For example in /etc/default/grub **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** should include any kernel boot parameters you want for normal boot or **GRUB_CMDLINE_LINUX=""** applies to both regular and (recovery) boot.  If you remove the **quiet** and **splash** you would see messages while you boot instead of a blank screen and then splash (actually plymouth now).

---

### Post by eraker on 2010-10-20
> **efflandt said:**
> 1. The xorg.conf file has not been used for awhile unless you specifically need one for something special (like special resolution not recognized automatically).  If you install proprietary video drivers [usually by activating them in System > Administration > Additional Drivers (or Hardware Drivers in earlier Ubuntu)] they usually provide a basic xorg.conf for that type of video.  Although, most settings can be made using the app that came with them, like Catalyst for ATI or NVIDIA X Server Settings for nVidia.

Thank you very much for your reply. The reason I asked is that I stupidly did a dist-upgrade (a series of them), which landed me in  a rough spot without a working display. I tried to hack together a working version of xorg, but was surprised to find a good sample did not exist on any of the livecds I launched. Further, all of the 10.10 amd64 livecds I tried (kubuntu, xubuntu, ubuntu) did  not actually display properly and I couldn't figure out how to adjust display settings. 

I will see to editing grub. (The changes make me a little nervous in case the system gets fried again, but I guess that's the price we pay for progress.)

---

