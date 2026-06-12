---
title: "Wine"
date: 2010-12-15
forum: General Help
---

### Post by hantechbl on 2010-12-15
when I try executing a file in WINE that was a C++ and was compiled into a .exe I get:
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"Z:\\home\\server\\ms\\MCServer.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\server\\ms\\MCServer.exe" failed, status c0000135

```
I just hear that I need MSVC9, is there an alternative?

---

### Post by branscombe_richmond on 2010-12-15
wine is useless for any modern application you may want to run.  likely you will have to search for the application at the wine website to see its status.

if you made it yourself, then just compile and execute it in a real life windows environment.  dual boot or run windows in a virtualbox and run from there.  put no faith into wine, ever.  wine may as well be a dead project.

---

### Post by hantechbl on 2010-12-15
Somebody made this in Microsoft visual Studio 9, is there any way that I can port it to linux?  I don't have the original C files.

---

### Post by sonatso on 2010-12-15
As suggested, check the status of the program on the Wine website; wine compatibility runs about a year behind. As for porting, depending on the program, that really isn't practical without the original source, experience with the program, and time to recode it.

---

### Post by kingchipo on 2010-12-15
"Somebody made this in Microsoft visual Studio 9, is there any way that I can port it to linux? I don't have the original C files."


its not going to be on winehq.... someone made it..

tried all your winetricks?

---

### Post by mc4man on 2010-12-15
not sure what ubuntu release you're using, if more recent than hardy then consider adding the  wine team ppa, 
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
package details for above
[https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages](https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages)

Then either update to latest of your current wine version and install winetricks or install the 1.3 wine (winetricks will be installed

then run winetricks from a terminal - screen shows some suggested for what you have

If on hardy you could search out using winetricks or locate the dll online and place in wines system32 folder (winetricks much better choice here.

Note: I only use wine for a few very modern progs which work fine - you may wish to request a mod to move this thread to the wine sub forum where you may be better advised

---

