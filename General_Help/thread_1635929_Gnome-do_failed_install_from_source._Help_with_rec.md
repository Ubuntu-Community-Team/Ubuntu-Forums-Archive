---
title: "Gnome-do failed install from source. Help with recovery requested!"
date: 2010-12-02
forum: General Help
---

### Post by dre12b on 2010-12-02
I was experiencing some funny issues with gnome-do, so I attempted to install from source. Following the instructions on the gnome-do website verbatim, I received several errors. Gnome-do was installed (in Gnome menu), but would not run. Realizing I was over my head and was out of time, I ran "sudo make uninstall", restarted my machine for good measure, then installed gnome-do from my software manager. It still won't run. Running gnome-do from terminal gives the same error as when I attempted to install from source:

Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] in <filename unknown>:0
  at Do.Core.PluginManager.Initialize () [0x00000] in <filename unknown>:0
  at Do.Do.Main (System.String[] args) [0x00000] in <filename unknown>:0

I used purged gnome-do and plugins, restarted, and reinstalled, but am experiencing the same problem.  Any help recovering from my goof will be greatly appreciated!

I'm running 10.10 maverick 32-bit.

---

### Post by directhex on 2010-12-03
> **dre12b said:**
> I was experiencing some funny issues with gnome-do, so I attempted to install from source. Following the instructions on the gnome-do website verbatim, I received several errors. Gnome-do was installed (in Gnome menu), but would not run. Realizing I was over my head and was out of time, I ran "sudo make uninstall", restarted my machine for good measure, then installed gnome-do from my software manager. It still won't run. Running gnome-do from terminal gives the same error as when I attempted to install from source:

Unhandled Exception: System.InvalidOperationException: Could not read add-in description
  at Mono.Addins.Addin.get_Description () [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] in <filename unknown>:0
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] in <filename unknown>:0
  at Do.Core.PluginManager.Initialize () [0x00000] in <filename unknown>:0
  at Do.Do.Main (System.String[] args) [0x00000] in <filename unknown>:0

I used purged gnome-do and plugins, restarted, and reinstalled, but am experiencing the same problem.  Any help recovering from my goof will be greatly appreciated!

I'm running 10.10 maverick 32-bit.

Try erasing ~/.local/share/gnome-do/plugins/

---

### Post by dre12b on 2010-12-03
Thanks - that worked.  I knew there had to be a folder lurking somewhere.

In the meantime I've been using Kupfer.  It's ugly as sin, but is simple and has a really extensive collection of plugins.  Ends up being more functional than gnome-do.  The biggest plus is that the Evolution plugin works.

---

