---
title: "Problem with MonoDevelop"
date: 2010-06-16
forum: General Help
---

### Post by husky83 on 2010-06-16
I have problem with Monodevelop...

> marcin@marcin-laptop:~$ monodevelop 
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7862): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=9)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7862): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7862): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Ide.dll could not be loaded:
     Assembly:   glib-sharp    (assemblyref_index=7)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7862): WARNING **: Could not load file or assembly 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
marcin@marcin-laptop:~$ 
:confused::confused::confused:

---

