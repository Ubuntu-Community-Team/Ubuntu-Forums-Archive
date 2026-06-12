---
title: "Running program with mono"
date: 2011-02-20
forum: General Help
---

### Post by Vinger on 2011-02-20
Hello,

I want to use a program, that runs windows and "linux with mono". 
I run Kubuntu 10.10.

> 
koen@Koen-Kubuntu:~/Documents/Software/SuperOneClick_1_6_5$ mono SuperOneClick.exe

** (SuperOneClick.exe:4191): WARNING **: The following assembly referenced from /home/koen/Documents/Software/SuperOneClick_1_6_5/SuperOneClick.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=2)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/koen/Documents/Software/SuperOneClick_1_6_5/).


** (SuperOneClick.exe:4191): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (SuperOneClick.exe:4191): WARNING **: Missing method EnableVisualStyles in assembly /home/koen/Documents/Software/SuperOneClick_1_6_5/SuperOneClick.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'


does anyone knows how to solve these errors?
I tried sudo, but that did the same...

Allready thanks!

---

### Post by veggen on 2011-02-20
Mono can't find Winforms assembly...
Try finding and installing packages libmono-winforms1.0-cil and libmono-winforms2.0-cil. You probably need only the second one though...

---

### Post by juanmatias on 2012-01-03
Ey, cool. Thanks. And you're right, the second one only needed.

And you need one more step to get ir working.... see here: [http://forum.xda-developers.com/showpost.php?p=8699742&postcount=537](http://forum.xda-developers.com/showpost.php?p=8699742&postcount=537)

---

