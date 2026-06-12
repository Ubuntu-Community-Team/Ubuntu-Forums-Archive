---
title: "Mono Problems"
date: 2011-10-16
forum: General Help
---

### Post by 7cardcha on 2011-10-16
Whenever I try to use Mono for whatever purpose(I have 2 different Ubuntu machines it works on neither of them) It gives this error:

WARNING: The runtime version supported by this application is unavailable.
Using default runtime: v1.1.4322
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory.

mscorlib.dll Is located in /usr/lib/mono/2.0/

When I copy and chmod it to the 1.0 directory it gives the following error:

imps@vostro:/usr/lib/mono/1.0$ mono /home/imps/Desktop/Terraria/Terraria.exe
WARNING: The runtime version supported by this application is unavailable.
Using default runtime: v1.1.4322

** (/home/imps/Desktop/Terraria/Terraria.exe:9757): WARNING **: The class System.Collections.Generic.Stack`1 could not be loaded, used in System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Terraria.Main ---> System.TypeLoadException: Could not load type 'Microsoft.Xna.Framework.Audio.SoundEffect' from assembly 'Microsoft.Xna.Framework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=842cf8be1de50553'.
  --- End of inner exception stack trace ---
  at Terraria.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 
 
BTW I did torrent Terraria to make it easier to run on linux but I own the game so I figured it was alright.

---

### Post by directhex on 2011-10-17
You're trying to run a .NET 4.0 app, and don't have .NET 4.0 libraries installed.

You need Ubuntu 11.10 for .NET 4.0 support.

---

