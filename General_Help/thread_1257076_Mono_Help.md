---
title: "Mono Help"
date: 2009-09-03
forum: General Help
---

### Post by CrusaderAD on 2009-09-03
I'm just about to give up on mono. It seems great but I keep getting this error when tring to run my project:

```
** (Project1.exe:29555): WARNING **: The following assembly referenced from /home/user/Desktop/project/bin/Project1.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic.Compatibility    (assemblyref_index=4)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/user/Desktop/project/bin/).


** (Project1.exe:29555): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic.Compatibility, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Project1.frmlogin' from assembly 'Project1, Version=1.0.3532.14113, Culture=neutral, PublicKeyToken=null'.
```

Any help please?

---

### Post by directhex on 2009-09-03
> **raptormanad said:**
> I'm just about to give up on mono. It seems great but I keep getting this error when tring to run my project:

```
** (Project1.exe:29555): WARNING **: The following assembly referenced from /home/user/Desktop/project/bin/Project1.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic.Compatibility    (assemblyref_index=4)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/user/Desktop/project/bin/).


** (Project1.exe:29555): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic.Compatibility, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Project1.frmlogin' from assembly 'Project1, Version=1.0.3532.14113, Culture=neutral, PublicKeyToken=null'.
```

Any help please?

[libmono-microsoft-visualbasic8.0-cil](apt:libmono-microsoft-visualbasic8.0-cil)

---

### Post by CrusaderAD on 2009-09-04
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
libmono-microsoft-visualbasic8.0-cil is already the newest version.
libmono-microsoft-visualbasic8.0-cil set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by directhex on 2009-09-04
> **raptormanad said:**
> ```
Reading package lists... Done
Building dependency tree
Reading state information... Done
libmono-microsoft-visualbasic8.0-cil is already the newest version.
libmono-microsoft-visualbasic8.0-cil set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Ah. **AH**. Sorry, I didn't read your message enough.

Your app is not a VB.NET app, it's a VB6 app compiled with a VB.NET compiler. Mono has no VB6 legacy support, and doesn't have the Microsoft.VisualBasic.Compatibility assembly

---

### Post by CrusaderAD on 2009-09-04
Bummer, thanks for the info.

---

### Post by CrusaderAD on 2009-09-09
How would you go about building a VB app from the ground up in Mono? Is it was easy as making a new project and just start coding / compiling?

---

### Post by directhex on 2009-09-09
> **raptormanad said:**
> How would you go about building a VB app from the ground up in Mono? Is it was easy as making a new project and just start coding / compiling?

Mmm, more or less. MonoDevelop supports VB.NET projects (although in 2.0 there's no VB.NET-compatible integrated GUI designer)

Just write some VB.NET, compile it, and run it

```
directhex@desire:/tmp$ cat test.vb 
Module HelloWorld
    Sub Main()
        System.Console.WriteLine( "boo, i r mono" )
    End Sub
End Module
directhex@desire:/tmp$ vbnc test.vb 
Visual Basic.Net Compiler version 0.0.0.5914 (Mono 2.4.2 - r)
Copyright (C) 2004-2008 Rolf Bjarne Kvinge. All rights reserved.


Assembly 'test, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' saved successfully to '/tmp/test.exe'.
Compilation successful
Compilation took 00:00:00.7180680
directhex@desire:/tmp$ mono test.exe 
boo, i r mono
directhex@desire:/tmp$ 
```

See?

---

### Post by CrusaderAD on 2009-09-10
Everything has got to be in .NET right? VB6 code is unsupported?

---

### Post by directhex on 2009-09-10
> **raptormanad said:**
> Everything has got to be in .NET right? VB6 code is unsupported?

Right. VB6 is "legacy" at best, and one of the worst blights on the face of technology as a whole at wors... at normal. VB6 is what's called "unmanaged" in this context, meaning it's platform-specific code (like a C app) rather than cross-platform "managed" code that runs in a framework (like a Java app). Mono supports managed code, but not unmanaged code.

---

