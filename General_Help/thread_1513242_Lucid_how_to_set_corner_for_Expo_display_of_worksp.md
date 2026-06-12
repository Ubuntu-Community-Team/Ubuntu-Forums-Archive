---
title: "Lucid: how to set corner for Expo display of workspaces"
date: 2010-06-19
forum: General Help
---

### Post by keithpeter on 2010-06-19
Hello All

I have a lucid stock install of Ubuntu, and the visual effects are set to Normal.

The Windows-E shortcut brings up the 'expo' display of all four workspaces in a line.

Is there a way of making (say) the top right corner of the screen sensitive so that moving the mouse there triggers the display of all workspaces? 

Can this be done with 'stock' installed software?

gconf-editor has a promising looking key called 'expo_edge' at 

/apps/compiz/plugins/expo/allscreens/options/expo_edge

but that might do something different.

Thanks

---

### Post by twisted_steel on 2010-06-19
Install the 'compizconfig-settings-manager' program.  It will show up in the System -> Preferences menu when it is installed.  Open it up and scroll down to the Desktop section.  Click on Expo.  On the next page, click on the 'None' button to the right of 'Expo Edge'.  This will allow you to set an edge or corner.

---

### Post by keithpeter on 2010-06-19
> **twisted_steel said:**
> Install the 'compizconfig-settings-manager' program.  It will show up in the System -> Preferences menu when it is installed.  Open it up and scroll down to the Desktop section.  Click on Expo.  On the next page, click on the 'None' button to the right of 'Expo Edge'.  This will allow you to set an edge or corner.

Hello twisted_steel

Thanks for this reply. Is there a way of setting the preference without installing the compizconfig program?

I'm assuming that a GUI settings manager is just writing a file somewhere?

---

### Post by twisted_steel on 2010-06-19
> **keithpeter said:**
> Hello twisted_steel

Thanks for this reply. Is there a way of setting the preference without installing the compizconfig program?

I'm assuming that a GUI settings manager is just writing a file somewhere?

Yes, set the expo_edge key to 'TopRight'.  The compizconfig program exposes an extremely large amount of options, so it is still worth checking out.

---

### Post by keithpeter on 2010-06-19
> **twisted_steel said:**
> Yes, set the expo_edge key to 'TopRight'.  

Thanks very much. I couldn't find the format of the key.

Cheers

---

