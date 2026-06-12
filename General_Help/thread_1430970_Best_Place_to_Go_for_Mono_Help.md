---
title: "Best Place to Go for Mono Help?"
date: 2010-03-16
forum: General Help
---

### Post by Ozzymandi on 2010-03-16
Hey Guys,

Trying to Use Mono to Run Qualcomm's BrewMP Simulator, I know it's a long shot but I figured I'd try.

So I installed
```
$sudo apt-get install mono-complete
```

Great, then I go to run my application:
```
$ ls
a1Host.dll        BREW_Tones.dll   en               ko              MFC71u.dll   NetSim.dat  SimCtrlLib.dll        SimulatorRes.dll
backlight.png     camera.dll       es               libEGL.dll      mif          pt          simulatorCore.ini     sys
BREWEncoding.dll  DataFiles        fr               libgles_cm.dll  mod          Qpl.dll     Simulator.dll         VoiceDB
BREWResCore.dll   debugoutput.png  hid_devices.cfg  libGLESv2.dll   msvcp71.dll  rom_vdb     Simulator.exe         zhcn
BrewRes.dat       dpkIcon.png      ja               libVG11.dll     msvcr71.dll  shared      Simulator.exe.config
escragg@ozzy-frogger /space/frogger/dev/GWTF/tools/brewMP/6.7/tools/simulation $ mono Simulator.exe

Unhandled Exception: System.DllNotFoundException: Simulator.dll
  at (wrapper managed-to-native) SimCtrlLib.SimCore:CSimCoreRegister (uint,uint,SimCtrlLib.UiItemEventHandlerDelegate,bool)
  at SimCtrlLib.SimCore.SimCoreRegister (UInt32 dwUserData, UInt32 dwEventCode, SimCtrlLib.UiItemEventHandlerDelegate eventHandler, Boolean bRegister) [0x00000] 
  at SimulatorApp.SimulatorAppForm.RegisterForSimulatorEvents () [0x00000] 
  at SimulatorApp.SimulatorAppForm.InitSimulator () [0x00000] 
  at SimulatorApp.SimulatorAppForm.InitializeFormAndStartSimulator () [0x00000] 
  at SimulatorApp.SimulatorAppForm..ctor (Boolean noShow, Boolean noSplash) [0x00000] 
  at (wrapper remoting-invoke-with-check) SimulatorApp.SimulatorAppForm:.ctor (bool,bool)
  at SimulatorApp.Program.Main (System.String[] args) [0x00000]
```

As you can see, the .dll it's complaining about not being able to find is right there in the PWD, which leads me to the fairly obvious conclusion that I'm being retarded and not setting (whatever .net's equivalent of) the classpath correctly.

Where's the best place to take this question?  It'd be awesome of I could dump my Virtualized XP Machine.

-Ozzy

---

