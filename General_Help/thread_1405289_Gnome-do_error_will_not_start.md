---
title: "Gnome-do error will not start"
date: 2010-02-12
forum: General Help
---

### Post by fatum on 2010-02-12
I love using the keyboard for everything possible and because of this I love the program Gnome-Do (plus I come from Mac and used Quicksilver.) Problem is when trying to start Gnome-Do on my desktop machine I get the following from terminal

```

UbuntuPro:~$ gnome-do
Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 


```

I am running the latest release of Gnome-Do (0.8.3.1) from their PPA on Karmic. Any advice or help with this issue would be greatly appreciated. Thank you in advance.

---

