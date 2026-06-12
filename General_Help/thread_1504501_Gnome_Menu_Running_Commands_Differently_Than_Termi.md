---
title: "Gnome Menu Running Commands Differently Than Terminal"
date: 2010-06-08
forum: General Help
---

### Post by ubernerd2048 on 2010-06-08
In order to get all of my games working without sound issues in WINE I rand winecfg via padsp and set the sound to OSS and also need to run the games themselves via padsp. I can do this via the terminal without issues but would prefer to not have to do so.

The default shortcut for World of Warcraft for instance runs the command:
env WINEPREFIX="/home/<username>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"

Running the command:
env WINEPREFIX="/home/<username>/.wine" padsp wine "C:\Program  Files\World of Warcraft\Launcher.exe"

from the terminal starts the game via the PulseAudio wrapper, however putting that exact same command into the gnome menu shortcut under the field "Command" does not run the game through padsp, it starts but only as if i had simply run "wine Launcher.exe" from the game's directory without running it through padsp.

This is not a sound or wine support issues, just wondering why the Gnome menu seems to preset such inconsistant behavior. (Probably me messing something up, but I'm hoping a kind soul here will take pity and show me the light. :))

---

### Post by dcstar on 2010-06-08
> **ubernerd2048 said:**
> 
..........
This is not a sound or wine support issues, just wondering why the Gnome menu seems to preset such inconsistant behavior. (Probably me messing something up, but I'm hoping a kind soul here will take pity and show me the light. :))

The Gnome environment is not a terminal environment.

If you want it launched in a terminal with all terminal functions, then create the launcher with the the terminal option - that is why it exists.

---

### Post by ubernerd2048 on 2010-06-08
You humble me sir. (I assume sir, apologies if that's not correct.) Thanks for the aforementioned taking of pity. Problem fixed by noticing the dropdown menu...... :(

---

