---
title: "Need help with Wine."
date: 2011-02-19
forum: General Help
---

### Post by Akso on 2011-02-19
Hello everyone, im trying to play a game under ubuntu with Wine
first of i installed wine and then got this problem when trying to run it:

[I]~/.wine/drive_c/Program Files/Stunlock Studios/Bloodline Champions/Binary$ wine BloodlineChampions.exe
fixme:actctx:p****_manifest_buffer root element is L"asmv1:assembly", not <assembly>
wine: Install the Windows version of Mono to run .NET executables[/I]

then i installed windows version of Mono with wine and now i get this error when trying to run the executable file:

[I]fixme:actctx:p****_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:actctx:p****_manifest_buffer root element is L"asmv1:assembly", not <assembly>
** Message: Unknown heap type: SmartAssembly


Unhandled Exception: System.InvalidProgramException: Invalid IL code in .?: (string[]): IL_0012: brfalse.s IL_001[/I]c


ne1 have any idea what to do ?

---

### Post by Frogs Hair on 2011-02-19
Hi and Welcome

I'm not a Wine user , but this may come in handy.[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by dino99 on 2011-02-19
welcome,

there is a special wine subforum , so post there next time

if there is nothing important into .wine, its better to erase it and start from scratch

install the latest wine with this ppa into synaptic repo (third parties): ppa:ubuntu-wine/ppa

( from: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa))

then update upgrade

about the needed mono: install it with winetricks into a terminal, before installing your app:

winetricks  , from the list check either mono26 or mono28 and apply

then you are ready to install your app (but you still can watch [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true) to find this app

---

### Post by marin123 on 2011-02-19
run it with mono.

```
mono YourApp.exe
```

it seems to be using .NET framework...

---

### Post by Akso on 2011-02-19
did all that and it doesnt seem to be working im getting the same errors.

---

### Post by marin123 on 2011-02-19
are you getting the same errors when you run it with mono? it seems a bit weird to get same error with two different applications.

---

### Post by Akso on 2011-02-19
no with mono the error msg is

[I]~/.wine/drive_c/Program Files/Stunlock Studios/Bloodline Champions/Binary$ mono BloodlineChampions.exe
** Message: Unknown heap type: SmartAssembly


Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for <Module> ---> System.InvalidProgramException: Invalid IL code in #c.#b:#bOd (): IL_0005: bne.un.s  IL_000e


  at <Module>..cctor () [0x00000] 
  --- End of inner exception stack trace ---[/I]

---

### Post by Akso on 2011-02-20
any idea ?

---

### Post by marin123 on 2011-02-20
> **Akso said:**
> any idea ?

no :(

---

### Post by jerenept on 2011-02-20
Install PlayOnLinux, and use it to install the MS .NET Framework in WINE..... 
Or, alternatively, maybe mono? but you've tried that already hmm.... :-k

---

