---
title: "inSSIDer not working in wine"
date: 2009-11-17
forum: General Help
---

### Post by GHOST_TUX on 2009-11-17
I just installed inSSIDer and Mono in wine (inSSIDer is a .net app) and when i try to run it nothing happens.  so i tried from the shell and here is what it outputted:

michael@michael-laptop:~$ wine start "c:/Program Files/MetaGeek/inSSIDer/bin/Inssider.exe"
fixme:exec:SHELL_execute flags ignored: 0x00000500
michael@michael-laptop:~$ wine: Call from 0x7b8453f0 to unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName, aborting
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xcb2ce7


any help with these error and what might be causing them?

---

### Post by t.alex on 2009-12-27
try ```
sh winetricks gdiplus
```
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

...if it's not too late :)

---

### Post by fabrixx on 2010-01-05
> **t.alex said:**
> try ```
sh winetricks gdiplus
```[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

...if it's not too late :)

 i receive:


```
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a060 0x1001818 1 0x33fe58 (null) (null) 0x100a068
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a080 0x1001808 1 0x33fe58 (null) (null) 0x100a088
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0a0 0x10017f8 1 0x33fe58 (null) (null) 0x100a0a8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0c0 0x10017e8 1 0x33fe58 (null) (null) 0x100a0c8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0e0 0x10017d8 1 0x33fe58 (null) (null) 0x100a0e8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a100 0x10017c8 1 0x33fe58 (null) (null) 0x100a108
fixme:win:RegisterDeviceNotificationW (hwnd=0x128898, filter=0x76e92c,flags=0x00000001),
    returns a fake device notification handle!
fixme:exec:SHELL_execute flags ignored: 0x00000100
Non &#65533; stato possibile eseguire l'applicazione, o nessuna applicazione &#65533; associata con il file specificato.
ShellExecuteEx fallito: Path not found
```

---

### Post by t.alex on 2010-01-05
you could try to install winbind
```
sudo apt-get install winbind

```

---

### Post by fabrixx on 2010-01-10
Thanks...but i.ve removed all.....

---

