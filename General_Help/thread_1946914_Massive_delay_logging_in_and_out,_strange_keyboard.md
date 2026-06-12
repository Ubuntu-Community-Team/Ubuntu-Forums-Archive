---
title: "Massive delay logging in and out, strange keyboard behaviour,  crashes."
date: 2012-03-25
forum: General Help
---

### Post by J V on 2012-03-25
When logging in (By checking a TTY with top running) for a good 30 seconds at least, init is the most CPU intensive process on the machine (At a whopping 0%)

There is no IO, X simply shows the display manager background, it takes a long time to log in.

Once logged in the keyboard layout may be US (What I have it set to) or US (International with dead keys) which the default was set to.

At one time I was able to switch between tty's with alt+arrow keys (Which caused problems with graphical applications)

Logging out makes the screen go black for about as long as logging in, when the display manager reappears my account isn't shown in the user list.

Attempting to log in via the "Other" option on the DM stops it responding.

I backed up and deleted my .config directory, but there was no change.

Logs suggest something was happening as they all have a large delay at around the same time, but I can't see what caused it.

The messages log is nowhere to be found.

Log example:
```
[    22.946] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    22.946] (**) Option "xkb_rules" "evdev"
[    22.946] (**) Option "xkb_model" "pc105"
[    22.946] (**) Option "xkb_layout" "us"
[    22.946] (**) Option "xkb_variant" "intl"
[   122.865] (II) Open ACPI successful (/var/run/acpid.socket)
[   122.925] (II) NVIDIA(0): Setting mode "nvidia-auto-select"

```In short: It's seriously not working and I have no idea why

Edit: A good deal of packages were "Available for upgrade" but wouldn't upgrade without force, upgrading them seems to have fixed the problem (I'm guessing half of something important got mismatched)

I'd still like to know what caused it (The alt+arrows thing was very strange) so I can stop it in future.

---

