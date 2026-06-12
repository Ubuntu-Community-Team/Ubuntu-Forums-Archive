---
title: "X-Lite 4.0 issue!!!!!!!!!!!!!!"
date: 2011-07-22
forum: General Help
---

### Post by Detroit_Bad_Boy on 2011-07-22
I had installed winetricks and it allowed me to install X-Lite 4.0 softphone which I need for my home based work. I attempted to run it from the fake C:/ location and this is the eroor I received in terminal:


** (X-Lite4.exe:31): WARNING **: The following assembly referenced from C:\Program Files\X-Lite4.exe could not be loaded:
     Assembly:   PresentationFramework    (assemblyref_index=0)
     Version:    3.0.0.0
     Public Key: 31bf3856ad364e35
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (C:\Program Files\).


** (X-Lite4.exe:31): WARNING **: Could not load file or assembly 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
The entry point method could not be loaded

I also downloaded mono 2.4.23 for windows which I also installed with winetricks. I had thought this would allow it to run in ubuntu. 
  Does anyone know how I can fix this problem? Or if there IS a fix for it??

UPDATE: I installed mono for linux as well as Microsoft C++ Visual Redistributable - x86  9.0.30729.17, which X-Lite required.
Now when I see it in fake C:/ through winefile and try to access it, I get this error (the other errors don't show up now):

The entry point method could not be loaded

My goal is to make X-Lite 4.0 ( a windows program) work within Ubuntu 11.04. If anyone knows of a way to fix this or make it operational, it would be most appreciated.

---

