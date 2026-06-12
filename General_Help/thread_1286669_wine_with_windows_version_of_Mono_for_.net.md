---
title: "wine with windows version of Mono for .net?"
date: 2009-10-09
forum: General Help
---

### Post by sdowney717 on 2009-10-09
SimpleCallerId.exe
scott2@scott2-desktop:~/Desktop$ wine SimpleCallerId.exe
install the Windows version of Mono to run .NET executables
scott2@scott2-desktop:~/Desktop$ 


any idea where do you get this?
I was looking for a callerid app

---

### Post by cb951303 on 2009-10-09
[http://ftp.novell.com/pub/mono/archive/2.4.2.3/windows-installer/3/mono-2.4.2.3-gtksharp-2.12.9-win32-3.exe](http://ftp.novell.com/pub/mono/archive/2.4.2.3/windows-installer/3/mono-2.4.2.3-gtksharp-2.12.9-win32-3.exe)

---

### Post by MauritsMB on 2009-10-22
I have a similar problem.
I downloaded and instaled the Windows version of mono for .net application using wine.
But how do I execute a .exe file with this?

Cheers

---

### Post by cb951303 on 2009-10-23
something like "wine /path/to/mono.exe /path/to/netApp.exe"
should work

---

### Post by kayas80 on 2009-11-06
I was tying to run an executable via wine and used to get the same message:

install the Windows version of Mono to run .NET executables.

I installed the mono-2.4.2.3-gtksharp-2.12.9-win32-3.exe as suggested above. Now when I run the executable I get the following error:

kayas80@kayas80:~$ env WINEPREFIX="/home/kayas80/.wine" wine "C:\Program Files\World of Warcraft\Interface\AddOns\WebDKP Sync.exe"
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x9a4, disabling mixer

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.MimeIconEngine ---> System.DllNotFoundException: libgdk-x11-2.0.so.0
  at (wrapper managed-to-native) System.Windows.Forms.GnomeUtil:gdk_init_check (intptr,intptr)
  at System.Windows.Forms.GnomeUtil.Init () [0x00000] 
  at System.Windows.Forms.GnomeUtil.GetIcon (System.String icon, Int32 size) [0x00000] 
  at System.Windows.Forms.GnomeHandler.AddGnomeIcon (System.String internal_mime_type, System.String name) [0x00000] 
  at System.Windows.Forms.GnomeHandler.CreateUIIcons () [0x00000] 
  at System.Windows.Forms.GnomeHandler.Start () [0x00000] 
  at System.Windows.Forms.MimeIconEngine..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Windows.Forms.WinFileSystem..ctor () [0x00000] 
  at System.Windows.Forms.MWFVFS..ctor () [0x00000] 
  at System.Windows.Forms.FileDialog..ctor () [0x00000] 
  at System.Windows.Forms.OpenFileDialog..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.OpenFileDialog:.ctor ()
  at WebDKPSync.MainForm.InitializeComponent () [0x00000] 
  at WebDKPSync.MainForm..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) WebDKPSync.MainForm:.ctor ()
  at WebDKPSync.Program.Main () [0x00000]

Can anyone help with this please?

---

### Post by keelx on 2011-07-26
Why not just use the ubuntu version of Mono? A .NET executable is not windows-native code, but a form of bytecode that can be run on any .NET platform. On windows, this is .NET. On mac and linux, this is Mono.
sudo apt-get install libmono-dev

---

### Post by TylerBraun on 2011-08-03
> **keelx said:**
> Why not just use the ubuntu version of Mono? A .NET executable is not windows-native code, but a form of bytecode that can be run on any .NET platform. On windows, this is .NET. On mac and linux, this is Mono.
sudo apt-get install libmono-dev

I tried this and it installed libmono-dev fine but nothing changed. I still get "wine: Install the Windows version of Mono to run .NET executables" when I try to run my program. In my case it is Impulse.exe

---

### Post by gandaran on 2011-08-03
> **TylerBraun said:**
> I tried this and it installed libmono-dev fine but nothing changed. I still get "wine: Install the Windows version of Mono to run .NET executables" when I try to run my program. In my case it is Impulse.exe
you don't use wine here just mono for .NET executables
```
mono application.exe
```

---

### Post by TylerBraun on 2011-08-03
Thanks for the quick reply :)

Unfortunatly when I tried that I got this:



```
** (Impulse.exe:6763): WARNING **: The following assembly referenced from /home/tyler/.wine/drive_c/Program Files/Impulse/Impulse.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/tyler/.wine/drive_c/Program Files/Impulse/).


** (Impulse.exe:6763): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Stardock.Central.Client.Program' from assembly 'Impulse, Version=3.30.4164.19374, Culture=neutral, PublicKeyToken=null'.
```



Any idea what that means and/or how to fix it? Will a reinstall fix it perhaps?

---

### Post by directhex on 2011-08-03
> **TylerBraun said:**
> Thanks for the quick reply :)

Unfortunatly when I tried that I got this:



```
** (Impulse.exe:6763): WARNING **: The following assembly referenced from /home/tyler/.wine/drive_c/Program Files/Impulse/Impulse.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/tyler/.wine/drive_c/Program Files/Impulse/).


** (Impulse.exe:6763): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Stardock.Central.Client.Program' from assembly 'Impulse, Version=3.30.4164.19374, Culture=neutral, PublicKeyToken=null'.
```



Any idea what that means and/or how to fix it? Will a reinstall fix it perhaps?

[libmono-winforms2.0-cil](apt:libmono-winforms2.0-cil)

---

### Post by TylerBraun on 2011-08-04
> **directhex said:**
> [libmono-winforms2.0-cil](apt:libmono-winforms2.0-cil)
I installed this. Should I still be use "mono application.exe"? When I did I got:
```
tyler@Wolfen:~/.wine/drive_c/Program Files/Impulse$ mono Impulse.exe

** (Impulse.exe:2514): WARNING **: The following assembly referenced from /home/tyler/.wine/drive_c/Program Files/Impulse/Gibraltar.Agent.dll could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=8)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/tyler/.wine/drive_c/Program Files/Impulse/).


** (Impulse.exe:2514): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
File name: 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'
  at Gibraltar.Monitor.Log.OnInitialize (Boolean suppressTraceInitialize) [0x00000] in <filename unknown>:0 
  at Gibraltar.Monitor.Log.Initialize (Boolean suppressTraceInitialize) [0x00000] in <filename unknown>:0 
  at Gibraltar.Monitor.Log.StartSession (IMessageSourceProvider sourceProvider, System.String reason) [0x00000] in <filename unknown>:0 
  at Gibraltar.Monitor.Log.StartSession (Int32 skipFrames, System.String reason) [0x00000] in <filename unknown>:0 
  at Gibraltar.Agent.Log.StartSession () [0x00000] in <filename unknown>:0 
  at Stardock.Central.Client.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

---

### Post by directhex on 2011-08-05
> **TylerBraun said:**
> I installed this. Should I still be use "mono application.exe"? When I did I got:
```
tyler@Wolfen:~/.wine/drive_c/Program Files/Impulse$ mono Impulse.exe

** (Impulse.exe:2514): WARNING **: The following assembly referenced from /home/tyler/.wine/drive_c/Program Files/Impulse/Gibraltar.Agent.dll could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=8)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/tyler/.wine/drive_c/Program Files/Impulse/).


** (Impulse.exe:2514): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
File name: 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'
  at Gibraltar.Monitor.Log.OnInitialize (Boolean suppressTraceInitialize) [0x00000] in <filename unknown>:0 
  at Gibraltar.Monitor.Log.Initialize (Boolean suppressTraceInitialize) [0x00000] in <filename unknown>:0 
  at Gibraltar.Monitor.Log.StartSession (IMessageSourceProvider sourceProvider, System.String reason) [0x00000] in <filename unknown>:0 
  at Gibraltar.Monitor.Log.StartSession (Int32 skipFrames, System.String reason) [0x00000] in <filename unknown>:0 
  at Gibraltar.Agent.Log.StartSession () [0x00000] in <filename unknown>:0 
  at Stardock.Central.Client.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

[libmono-microsoft-visualbasic8.0-cil](apt:libmono-microsoft-visualbasic8.0-cil)

---

### Post by TylerBraun on 2011-08-06
Well. That changed things:```
tyler@Wolfen:~/.wine/drive_c/Program Files/Impulse$ mono Impulse.exe
Killed

```
I'm hoping this isn't a dead end. :(

---

