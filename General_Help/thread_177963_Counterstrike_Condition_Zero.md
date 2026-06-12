---
title: "Counterstrike: Condition Zero"
date: 2006-05-17
forum: General Help
---

### Post by nolongerlivecd on 2006-05-17
Hey guys, it's me back again about CS:CZ. 

I got it to actually load, but it has no fonts, and I can't see what I'm typing for the reg key. But anyway, here's my output:

Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fdc5dd8)->((nil),00000008)
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fdc5dd8)->((nil),00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"Z:\\MEDIA\\HDA5\\VALVE\\CONDITION".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"Z:\\MEDIA\\HDA5\\VALVE\\CONDITION".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1


I got this terminal output after typing: wine (path to cs)/hl.exe -game czero -width (screen pixels width) -height (screen pixels height) -gl

I run it with OpenGL by the way.

---

