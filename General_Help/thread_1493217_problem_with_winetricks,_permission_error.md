---
title: "problem with winetricks, permission error??"
date: 2010-05-25
forum: General Help
---

### Post by violetdream on 2010-05-25
Hi everyone, I'm getting this error with winetricks. I tried installing wine from source and reinstalling and nothing worked. What's going on?? :(
```

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x76e958): stub
fixme:service:EnumServicesStatusW 0x1220b0 type=30 state=3 (nil) 0 0x76e7e8 0x76e7f4 0x76e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x76e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x121ee0,(nil)): stub
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x547d74
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fe18, (null), (null), 0x100a068,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fe18, (null), (null), 0x100a088,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fe18, (null), (null), 0x100a0a8,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fe18, (null), (null), 0x100a0c8,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fe18, (null), (null), 0x100a0e8,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fe18, (null), (null), 0x100a108,)
fixme:win:RegisterDeviceNotificationW (hwnd=0x124b10, filter=0x54e93c,flags=0x00000001) returns a fake device notification handle!
/usr/bin/winetricks: 3717: cannot create /home/stacia/.wine/dosdevices/c:/winetrickstmp/zenity.sh: Permission denied
/usr/bin/winetricks: 3717: cannot create /home/stacia/.wine/dosdevices/c:/winetrickstmp/zenity.sh: Permission denied
sh: Can't open /home/stacia/.wine/dosdevices/c:/winetrickstmp/zenity.sh

```

---

### Post by violetdream on 2010-05-25
nevermind, 
```
~/.wine/drive_c$ sudo chmod 777 winetrickstmp/
```

this worked.

---

