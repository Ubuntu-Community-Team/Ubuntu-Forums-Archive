---
title: "Ubuntu 9.10 monodevelop fails to start"
date: 2009-12-12
forum: General Help
---

### Post by cblair2k2 on 2009-12-12
I have version 8.10 Ubuntu but have upgraded it to now Ubuntu 9.10 through the update manager.  I had monodevelop working prior but it seems ever since I had upgraded the kernel and went to Karmic Koala my monodevelop won't start. I have tried to fully uninstall it with the Ubuntu software center and removing all packages in synaptic package manager, then reinstalling it by either using the software center, or synaptic. Both ways give the same results. It gives many errors about mono.addins saying can't find it in the GAC, MONO_PATH or anywhere else, then finally has a FileNotFound Exception at the end. I don't have the output now because I am not on that PC, but what version is suppose to work with Ubuntu 9.10 and is there a specific way I need to install it??

I will post the specific output from the terminal later today.

WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=7)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Ide.dll could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.exe could not be loaded:
     Assembly:   Mono.Addins    (assemblyref_index=3)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: Could not load file or assembly 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:2552): WARNING **: Missing method get_Registry in assembly /usr/lib/monodevelop/bin/MonoDevelop.exe, type Mono.Addins.AddinManager

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'

---

