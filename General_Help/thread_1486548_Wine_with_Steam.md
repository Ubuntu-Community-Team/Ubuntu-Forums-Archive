---
title: "Wine with Steam"
date: 2010-05-18
forum: General Help
---

### Post by zeug on 2010-05-18
I have been trying to install Steam with Wine but 
```
msiexec /i SteamInstall.msi
``````
fixme:sfc:SfcIsKeyProtected ((nil), (null)) stub
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x32e4b0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x146940,(nil)): stub
err:eventlog:ReportEventW L"=====================================================\r\nException code: C0000005 ACCESS_VIOLATION\r\nFunction: 0x0\r\n=====================================================\r\n\r\nRegisters:\r\nEAX:00000000  EBX:004BEF2D  ECX:0032E4EC  EDX:00000031  ESI:0032E674  EDI:00000000\r\nCS:EIP:0073:00000000 "...
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

I have already search the forums but did not find a solution.  Also, I have tried to install Steam with Wine-Doors but it fails with "Invalid Command Parameters".

Thanks.

---

### Post by dvlchd3 on 2010-05-18
That is really weird.  I've never had a problem install Steam, and according to WineHQ AppDB, Steam is "Gold" ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163)).

Are you installing steam as a part of CSS or another game?  I've never tried to install Steam stand-alone, but Counter Strike Source always installed fine (and Steam came along for the ride).

---

### Post by zeug on 2010-05-18
I am just installing Steam on its own.  I plan on installing Portal with it, though.

EDIT I just noticed there is a Wine subforum, should this be moved there?

---

### Post by zeug on 2010-05-19
Bump.

---

### Post by zeug on 2010-05-20
Just to clarify about the wine-doors method, it actually says "Invalid command line parameters" in a prompt window.  The same thing happens when I try ```
wine start SteamInstall.msi
```but I get this in the terminal as output along with that same prompt window
```

fixme:exec:SHELL_execute flags ignored: 0x00000500

```Thanks.
zeug.

---

