---
title: "banshee mtp creative zen problems"
date: 2010-03-07
forum: General Help
---

### Post by piratemurray on 2010-03-07
Banshee can't connect to my Creative Zen 4GB music player via MTP.

I'm running the latest daily builds of Banshee from the PPA. Rhythmbox works and syncs fine.

I'm running Lucid Lynx 64bit.

Banshee outputs this when I run it from the terminal.

```
[Warn  18:20:31.837] Hardware manager extension failed to load - Exception has been thrown by the target of an invocation.
[Warn  18:20:31.837] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
[Warn  18:20:31.840] Caught an exception - No HardwareManager extensions could be loaded. Hardware support will be disabled. (in `Banshee.Services')
  at Banshee.Hardware.HardwareManager..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
[Warn  18:20:34.131] Caught an exception - Object reference not set to an instance of an object (in `Banshee.AudioCd')
  at Banshee.AudioCd.AudioCdService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  18:20:34.131] Extension `Banshee.AudioCd.AudioCdService' not started: Object reference not set to an instance of an object
[Warn  18:20:34.136] Caught an exception - Object reference not set to an instance of an object (in `Banshee.AudioCd')
  at Banshee.AudioCd.AudioCdService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  18:20:34.136] Extension `Banshee.AudioCd.AudioCdService' not started: Object reference not set to an instance of an object
```

Any suggestions?

---

### Post by piratemurray on 2010-03-09
Update on this for anyone interested. Banshee has now connected on the second attempt.

First attempt-----> nothing
Second attempt ------> after a bit Banshee connected and I can see my files on my Creative Zen

Didn't connect on the second Banshee start up straight away. I had to wait for this:

```
Device 0 (VID=041e and PID=4150) is a Creative ZEN V.
PTP_ERROR_IO: Trying again after re-initializing USB interface
```

---

### Post by piratemurray on 2010-03-09
Sad times :(

Connected but won't transfer files across. Massive output to the terminal though. 

I'm filing a bug report if you're interested.

Here you go!

[bug report on launchpad #535268]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/535268")

---

