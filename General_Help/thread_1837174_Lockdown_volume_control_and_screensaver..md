---
title: "Lockdown volume control and screensaver."
date: 2011-09-01
forum: General Help
---

### Post by CallsignBaron on 2011-09-01
Need some help.

I have a computer deployed in a public location with a guest account. I have used Pessulus to lock it down as best as it can but its features are very limited. I need more control over this system.

My particular problem recently is I have an unknown user that somehow changes the sound volume settings and turns off the screensaver. This computer is in a public area and the volume needs to be limited. I do this with alsamixer by limiting the PCM control. The volume control on the panel is locked out with Pessulus and the the menu is very limited so as not to show the terminal, but once I edit the menu, I can't find a way to hide the "Edit Menus" option in the right click menu so I think this may be how this user is gaining access. Is there a way to lockdown the volume controls so that only root has control? I have tried changing permissions on gnome-sound-control even and cannot lock this down.

The same situation is occurring in the screensaver settings. The user is gaining access to these settings and disabling the screensaver. Surely there must be some administrator type options to lockdown this system.

Any help would be greatly appreciated.

Thank you.

---

### Post by Frogs Hair on 2011-09-01
As you know , both settings are accessible to any user . One approach may be to remove the volume control from the panel and remove the check for both from the main menu. At least they would no longer appear on the menu or panel . You would still have volume access via Rythmbox or Banshee .

I don't know how you could give sound and the screen-saver administrative permissions . It seems to me if the screen saver is being disabled this person could be watching videos and you can remove video devices from permissions in Users and Groups .

---

### Post by CallsignBaron on 2011-09-01
Thanks Frogs Hair. I have removed the volume icon already and there are very few programs available in the menu, I have them all hidden. The problem with this route is that if you right click the menu, you still get the option to "Edit Menus". I have not found a way to hide this in the right click menu.

---

