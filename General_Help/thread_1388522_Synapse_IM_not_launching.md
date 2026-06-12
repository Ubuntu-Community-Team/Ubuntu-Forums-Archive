---
title: "Synapse IM not launching"
date: 2010-01-23
forum: General Help
---

### Post by dragonboss on 2010-01-23
Ok so i saw synapse im on ubuntu unleashed some time ago and decided to try it cos it looked cool downloaded the repo key added it and installed via terminal launch and nothing in the terminal it gives this:

** (/usr/lib/synapse/Synapse.exe:4705): WARNING **: The following assembly referenced from /usr/lib/synapse/Synapse.exe could not be loaded:
     Assembly:   qt-dotnet    (assemblyref_index=0)
     Version:    4.4.0.0
     Public Key: 194a23ba31c08164
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/synapse/).


** (/usr/lib/synapse/Synapse.exe:4705): WARNING **: Could not load file or assembly 'qt-dotnet, Version=4.4.0.0, Culture=neutral, PublicKeyToken=194a23ba31c08164' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Synapse.QtClient.Client' from assembly 'Synapse, Version=0.1.3431.34164, Culture=neutral, PublicKeyToken=null'.
 
How do i fix this thanks

---

### Post by brigdonnwr on 2010-02-28
I have exactly the same problem, running Linux mint 8 X64...would love to be able to give this a spin!

Thanks

---

### Post by recyclebin on 2010-06-09
I used to get the same error. After doing **export MONO_PATH=/usr/lib/cli/qt-dotnet-4.5/**, it started giving me the following error. Any leads on this?

```
** (/usr/lib/synapse/Synapse.exe:18080): WARNING **: Missing method .ctor in assembly /usr/lib/synapse/Synapse.exe, type Qyoto.NoArgDelegate

** (/usr/lib/synapse/Synapse.exe:18080): WARNING **: The class Qyoto.NoArgDelegate could not be loaded, used in Synapse

** (/usr/lib/synapse/Synapse.exe:18080): WARNING **: Missing method .ctor in assembly /usr/lib/synapse/Synapse.exe, type Qyoto.NoArgDelegate

Unhandled Exception: System.TypeLoadException: Could not load type 'Qyoto.NoArgDelegate' from assembly 'Synapse'.
  at Synapse.QtClient.Client.Main (System.String[] args) [0x00000] in /build/buildd/synapse-0.1-0+git370/src/Synapse.QtClient/Main.cs:52
```

---

