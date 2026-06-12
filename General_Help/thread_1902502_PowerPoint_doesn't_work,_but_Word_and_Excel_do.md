---
title: "PowerPoint doesn't work, but Word and Excel do"
date: 2011-12-30
forum: General Help
---

### Post by layers on 2011-12-30
This is what I get when I try to launch powerpoint. Am I missing some installations?
```
ibo@ibo-vaio:~$ wine "C:\Program Files\Microsoft Office\Office12\POWERPNT.exe"
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000007d0,(nil),0x0002,0x00000000,0x32ef28,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000007d0,(nil),0x0002,0x00000000,0x152318,(nil)): stub
err:eventlog:ReportEventW L"Microsoft Office PowerPoint"
err:eventlog:ReportEventW L"PowerPoint failed to launch in safe mode. Do you want to start Detect and Repair?"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:msimtf:DllGetClassObject ({c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} {00000001-0000-0000-c000-000000000046} 0x3287d0)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {c1ee01f2-b3b6-4a6a-9ddd-e988c088ec82} could be created for context 0x1
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:win:EnumDisplayDevicesW ((null),0,0x329fe0,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x800ee 0x00000000
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Sessions"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x00001b5b,(nil),0x0004,0x00000000,0x32a530,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
ibo@ibo-vaio:~$ 
```

---

### Post by layers on 2011-12-30
It was already a known problem. This is how I fixed it:

[QUOTE=http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992]In the Libraries tab in the area labeled "New override for library" type in riched20.dll and click on Add.

You will see it appear in the list below. Now select the riched20 in the list that we just added and click on the Edit button.

Set it to Native (Windows) and click OK.

This will allow Powerpoint and the other applications to run correctly.[/QUOTE]

---

