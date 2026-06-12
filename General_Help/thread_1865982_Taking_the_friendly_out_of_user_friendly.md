---
title: "Taking the friendly out of user friendly?"
date: 2011-10-20
forum: General Help
---

### Post by jo4hnc on 2011-10-20
I've been having a problem with Unity, Compiz and getting the graphics to work correctly. When I boot up my splash screen is just a series of vertical lines with what is probably the Ubuntu logo in the center. Photo attached.

I reset Unity and received this message:Attached.

When I try to open the Unity plug in in CSSM, I get this message:

"The new value for the key binding for the action Key to start the switcher in reverse in plugin Ubuntu Unity Plugin conflicts with the action Prev window of the Static Application Switcher plugin. 
Do you wish to disable Prev window in the Static Application Switcher plugin?"

Additionally, occasionally when I boot or restart the machine, all I get is the Unity bar at the top of the screen. The icons on the left are non existent and the Dash is not there.

Another interesting item is that when I look at the Nvidia X Server settings, in the X Server Display Configuration I see this:

"Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0." 

I do kind of like Unity(but not the fact that it's tough to configure)and really don't want to go back to Gnome but if I have to I guess I have to. Thanks in advance for any help you can provide.

John C

Processor AMD Athlon(tm) 64 Processor 3200+
Graphics Card GeForce 6600/PCI/SSE2 
OS 64-bit
Memory 3.9 GiB

---

### Post by jo4hnc on 2011-10-20
I tried to attach this info about resetting Unity but it didn't show.

-------@j-------desktop:~$ unity --reset

Checking if settings need to be migrated ...no

Checking if internal files need to be migrated ...yes

[LOG]: Moving Internal Files

[LOG]: Copying subdirectory from /home/jaycee/.compiz/session to /home/jaycee/.compiz-1/session

[LOG]: Copied file /home/jaycee/.compiz/session/10f06c639bdfaa3bf7131908919714164300000024490041 to /home/jaycee/.compiz-1/session/10f06c639bdfaa3bf7131908919714164300000024490041

[LOG]: Successfully moved internal files

Backend     : gconf

Integration : true

Profile     : default

Adding plugins

Skipping upgrade com.canonical.unity.unity.01.upgrade

Skipping upgrade com.canonical.unity.unity.02.upgrade

Initializing core options...done

Initializing bailer options...done

Initializing detection options...done

Initializing composite options...done

Initializing opengl options...done

Initializing decor options...done

Initializing mousepoll options...done

Initializing vpswitch options...done

Initializing animation options...done

Initializing snap options...done

compiz (expo) - Warn: failed to bind image to texture

Initializing expo options...done

Initializing move options...done

Initializing place options...done

Initializing grid options...done

Initializing gnomecompat options...done

Initializing wall options...done

Initializing ezoom options...done

Initializing workarounds options...done

Initializing staticswitcher options...done

Initializing resize options...done

Initializing fade options...done

Initializing scale options...done

Initializing session options...done

Starting unity-window-decorator

compiz (core) - Warn: no exact match for ConfigureNotify on 0x4000090!

compiz (core) - Warn: expected the following changes:

compiz (core) - Warn: sibling: 0x43ee95

compiz (core) - Warn: instead got:

compiz (core) - Warn: x: 0

compiz (core) - Warn: y: 0

compiz (core) - Warn: width: 1680

compiz (core) - Warn: height: 1050

compiz (core) - Warn: above: 0

compiz (core) - Warn: this should never happen. you should probably file a bug about this.

Window manager warning: Failed to load theme "Adwaita": Failed to find a valid file for theme Adwaita



Setting Update "main_menu_key"

Setting Update "run_key"

Setting Update "run_command_terminal_key"

Setting Update "fullscreen_visual_bell"

---

