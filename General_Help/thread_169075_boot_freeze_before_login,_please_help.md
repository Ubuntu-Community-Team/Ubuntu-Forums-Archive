---
title: "boot freeze before login, please help"
date: 2006-05-01
forum: General Help
---

### Post by brewman99 on 2006-05-01
I installed breezy on my system with no problems, however, the system freezes during the boot process. All goes well during the initial ubuntu splash screen, then the screen goes to black and a small white dot with rotating dashes appears in the middle of the screen. at this point the system freezes and a hard shut down is the only way to reboot. The sytem will boot in recovery mode with no problem. I have also run "sudo dpkg-reconfigure xserver-xorg" and i believe that my video driver settings are correct. when I attempt "sudo dpkg-reconfigure gdm", I get the following message:

*Reloading GNOME Display Manager configuration...
*Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

I have also noticed that before the splash screen, there is a message that says:
"unable to locate RSDP"

I don't know if any of this is relevant info, but i would like to give as much to work with as i can.

Any assistance is greatly appreciated.

---

### Post by magikasheep on 2008-06-25
i get the same problem. i boot through recovery to fix it shortly. sometimes it boots. if there is a solution please specify

i heard somewhere that it may be the screen resolution on startup. so change the setting in startup manager and see if that helps. i havent confirmed this yet, but i hope it helps (edit: this didnt fix it)

---

