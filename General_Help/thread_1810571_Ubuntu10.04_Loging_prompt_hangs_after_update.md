---
title: "Ubuntu10.04: Loging prompt hangs after update"
date: 2011-07-23
forum: General Help
---

### Post by shailesh07 on 2011-07-23
Hi,
I ran apt-get update to fetch firefox5. I didn't updated ubuntu since long so it down loaded around 280 updates including firefox. Now while installing I saw once EULA acceptance message for Microsoft ttf font installation, this message window doesn't have any button etc to confirm, so I did ctrl+c to exit, and then "apt-get" seems to have terminated in terminal.But I checked that it is still running in the background in process list, not sure active process or not.

I did rebooted PC assuming update might have completed. Now after reboot it boots up to the login prompt, but I don't see any cursor movement or key stroke effect. It just stays there and then after some time shuts down, with flashing error message relate to "Init.." i couldn't read it completely.

Can anyone please help?

- Shailesh

---

### Post by 2F4U on 2011-07-23
Can you get to a virtual console using Ctrl-Alt-Fx (x=1, 2, ...)? It seems as if the update was not finished and your system is now only half-updated. If you can open a virtual console, try to finish the update before you do anything else. Do you have proprietary video drivers installed? The updates probably brought in a new kernel, so there may be a problem with old proprietary video drivers.

---

### Post by shailesh07 on 2011-07-25
> **2F4U said:**
> Can you get to a virtual console using Ctrl-Alt-Fx (x=1, 2, ...)? It seems as if the update was not finished and your system is now only half-updated. If you can open a virtual console, try to finish the update before you do anything else. Do you have proprietary video drivers installed? The updates probably brought in a new kernel, so there may be a problem with old proprietary video drivers.
I tried to open virtual console with key combo you mentioned. I don't see any panel. It just stays dead at login screen. I tried to run in recovery mode, their it runs up to /script/init_bottom and then hangs there, no further progress.

Also i generally use vlc only, no proprietary drivers are installed.

-Thanks

---

### Post by dino99 on 2011-07-25
if it hangs at "/script/init_bottom " then the first idea coming is some acpi conflicts:

on the boot line, add either: nomodeset or noacpi

if one of them works, then make it permanent:

sudo gedit /etc/defaulr/grub
( add before "quiet splash" )

and then: sudo update-grub

if that fails again: remove "quiet splash" to see the details

note: on single OS system, hold "shift" key down at bios end process to see the grub menu

---

### Post by shailesh07 on 2011-07-27
dino99,

I am unable to login, how can I modify grub script/ Also I think it does complete(or part of it) /script/init_bottom as I see one "Done" message after that, while run in recovery mode.

---

