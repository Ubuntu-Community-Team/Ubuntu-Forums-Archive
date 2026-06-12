---
title: "Banshee starts and it's all grey"
date: 2009-07-17
forum: General Help
---

### Post by Patricrawley on 2009-07-17
Not like Not Responding grey, the window space, everything but the title bar is grey. When I run banshee from the terminal this is the output:
```

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.UnknownMethod: Method "Present" with signature "" on interface "org.bansheeproject.Banshee.ClientWindow" doesn't exist
  at IClientWindowProxy.Present () [0x00000] 
  at Halie.Client.HandleWindowCommands (Boolean present) [0x00000] 
  at Halie.Client.Main () [0x00000] 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] 
  at Booter.Booter.Main () [0x00000] 

```
I'm running 64 bit 9.04 and I installed banshee from it's own ppas

---

### Post by Patricrawley on 2009-07-19
bump

---

### Post by kostkon on 2009-07-19
Did you try reinstalling it?

---

### Post by Patricrawley on 2009-07-20
Twice, once I just reinstalled the second I did a complete removal and installed clean

---

### Post by Patricrawley on 2009-07-20
It still plays when I select play from the tray, it just wont show anythig in the window.

---

### Post by Chemical Imbalance on 2009-07-20
This happened to me once.  I restarted the machine and everything was normal again.  It was an odd one-off.

---

### Post by Patricrawley on 2009-07-20
I've restarted multiple times. I've totally shut down and I've booted in and out of Windows

---

### Post by Patricrawley on 2009-07-21
bump

---

### Post by Chemical Imbalance on 2009-07-21
Maybe you should file a bug report.

---

### Post by Patricrawley on 2009-07-21
I did, no response yet

---

