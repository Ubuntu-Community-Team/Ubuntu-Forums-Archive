---
title: "Gnome Do Does Not Open"
date: 2010-06-18
forum: General Help
---

### Post by zzzBrett on 2010-06-18
Gnome-do doesn't open for me. When I try from terminal, i get:

```

Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at Do.Core.PluginManager.Initialize () [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 
```

Any ideas?

---

### Post by zzzBrett on 2010-06-19
bump

---

