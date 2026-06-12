---
title: "Winner Poker at IPoker working?"
date: 2010-02-02
forum: General Help
---

### Post by jaansson on 2010-02-02
Hello!

I've been looking around for hours for a fix for this. Installing the Winner Poker client works out just fine through Wine. It's really slow though, and takes time for the installation windows to pop up and stuff. But it's working. But when I press the account creation thing, it just fails loading. I get a pop up inside the poker software, saying the page could not be loaded. It's a IE page. Same thing happens with the Nordicbet poker client, but I could register my account on the website through their browser version there. They havn't got that option at Winner.

So, anyway, I tried going to the wine appdb looking for some kind of guide, but there wasn't any. But there were a few guides for other IPoker clients. So, since Winner is powered by IPoker I looked through a few of them. And at the Titan Poker one they said that I needed ies4linux. So I tried that but it crashed, probably due to being really old. So I tried the same with winetricks, but with no good result. I probably even had it before since an actual IE site popped up during my account registraion.

So, basically, my question is: How do I get my poker client to successfully interract with the IE installation? And has anyone had this problem before and managed to solve it? (I'm sure I'm not the first one, since I've found people with this problem during my countless searches, just havn't found a fix that is working for me yet.) 

Thank you very much in advance!


EDIT:

This is the message that I get in the terminal btw:

```
danne@danne-laptop:~$ wine '/home/danne/.wine/dosdevices/c:/Poker/Winner Poker/casino.exe'mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
mmap() failed: Kan inte allokera minne
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xc69438,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusA 0x1e1328 type=30 state=1 0xc691e4 240 0xc69428 0xc69430 0xc69424
fixme:ras:RasEnumEntriesW ((nil),(null),0x1e16f0,0xc69100,0x1e13dc),stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e6610,0x1e51c8): stub
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:mountmgr:harddisk_ioctl unsupported ioctl 7c088
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msimtf:DllGetClassObject ({50d5107a-d278-4871-8989-f4ceaaf59cfc} {00000001-0000-0000-c000-000000000046} 0x32cc44)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {50d5107a-d278-4871-8989-f4ceaaf59cfc} could be created for context 0x401
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xc6e980,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:ntdll:RtlpWaitForCriticalSection section 0x961548 "?" wait timed out in thread 0026, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x961548 "?" wait timed out in thread 002b, blocked by 0009, retrying (60 sec)
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xc4be948,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
fixme:keyboard:X11DRV_GetKeyboardLayout couldn't return keyboard layout for thread 0009
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x32f364) using GetSystemInfo()
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xd16e948,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusA 0x24e1fc0 type=30 state=1 0xd16e6f4 240 0xd16e938 0xd16e940 0xd16e934
fixme:crypt:CRYPT_RegControl 4: stub
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:wintrust:HTTPSCertificateTrust (0x230c578)
fixme:wintrust:HTTPSFinalProv (0x230c578)
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xc4be948,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:crypt:CRYPT_RegControl 4: stub
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xfe2e980,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:wintrust:HTTPSCertificateTrust (0x2553f18)
fixme:wintrust:HTTPSFinalProv (0x2553f18)
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -524, flags 0x2!
fixme:ras:RasEnumConnectionsW (0x14ccd8,0xfe2e980,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusA 0x254d4b8 type=30 state=1 0xfe2e72c 240 0xfe2e970 0xfe2e978 0xfe2e96c
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -524, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -5511, flags 0x2!
fixme:crypt:CRYPT_RegCloseStore Unimplemented flags: 00000001
fixme:crypt:CRYPT_MemCloseStore Unimplemented flags: 00000001
fixme:crypt:CRYPT_RegCloseStore Unimplemented flags: 00000001
fixme:crypt:CRYPT_MemCloseStore Unimplemented flags: 00000001
fixme:ras:RasEnumEntriesW ((nil),(null),0x21e1b90,0xeae648,0x230fb8c),stub!
danne@danne-laptop:~$ 

```


And this, perhaps more interresting result came up when I ran the command: env WINEPREFIX='/home/danne/.wine/dosdevices/c:/Program Files/Internet Explorer/IEXPLORER.EXE' wine '/home/danne/.wine/dosdevices/c:/Poker/Winner Poker/casino.exe'


```
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x217778)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x53bdfd0)->(0x32f248 0x32f234 0)
fixme:shdocvw:ClientSite_GetContainer (0x217778)->(0x32f2ac)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x217778)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec (0x217778)->((null) 25 2 0x32f1b8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x217778)->((null) 26 2 0x32f1b8 (nil))
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x537e388)->(0x32e844)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x537e388)->(0x32e844)
fixme:mshtml:nsChannel_GetResponseHeader (0x537e388)->(0x32e80c 0x32e79c)
fixme:mshtml:nsChannel_GetResponseHeader (0x537e388)->(0x32e92c 0x32e94c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x217778)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x217778)->((null) 28 2 0x32f544 (nil))
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f0f4:3; TargetFrameName 0x32f114:8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x5568b00)->((nil))
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:urlmon:InternetBindInfo_GetBindString not supported string type 12
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x55cfe08)->(0x32e4d4)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x55cfe08)->(0x32e4d4)
fixme:mshtml:nsChannel_GetResponseHeader (0x55cfe08)->(0x32e49c 0x32e42c)
fixme:mshtml:nsChannel_GetResponseHeader (0x55cfe08)->(0x32e5bc 0x32e5dc)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x568a6d0)->(0x32e844)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x568a6d0)->(0x32e844)
fixme:mshtml:nsChannel_GetResponseHeader (0x568a6d0)->(0x32e80c 0x32e79c)
fixme:mshtml:nsChannel_GetResponseHeader (0x568a6d0)->(0x32e92c 0x32e94c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x5385df8)->(0x32e844)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x5385df8)->(0x32e844)
fixme:mshtml:nsChannel_GetResponseHeader (0x5385df8)->(0x32e80c 0x32e79c)
fixme:mshtml:nsChannel_GetResponseHeader (0x5385df8)->(0x32e92c 0x32e94c)
fixme:mshtml:nsChannel_SetReferrer (0x52fe770)->(0x4ef3fd8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4a9c3e8)->(0x32f248 0x32f234 0)
fixme:mshtml:nsChannel_SetReferrer (0x52c5500)->(0x4ef3fd8)
fixme:mshtml:nsChannel_SetReferrer (0x53fad98)->(0x4ef3fd8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x52c5548)->(0x32eed8 0x32eec4 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x54562d8)->(0x32eed8 0x32eec4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x217778)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f4a4)
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec (0x217778)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f4a4)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x556f3d0)->(0x32e4d4)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x556f3d0)->(0x32e4d4)
fixme:mshtml:nsChannel_GetResponseHeader (0x556f3d0)->(0x32e49c 0x32e42c)
fixme:mshtml:nsChannel_GetResponseHeader (0x556f3d0)->(0x32e5bc 0x32e5dc)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x51edab8)->(0x32e844)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x51edab8)->(0x32e844)
fixme:mshtml:nsChannel_GetResponseHeader (0x51edab8)->(0x32e80c 0x32e79c)
fixme:mshtml:nsChannel_GetResponseHeader (0x51edab8)->(0x32e92c 0x32e94c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x4f73a90)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x56cd5f8)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x56e24b0)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
fixme:wininet:INET_QueryOption Stub for 5
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x53bdf60)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:shdocvw:ClOleCommandTarget_Exec (0x4911e78)->((null) 26 2 0x32ecd4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4911e78)->((null) 29 2 0x32ece4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4911e78)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4911e78)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4911e78)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x4911e78)->(L"Done")
fixme:mshtml:nsChannel_IsNoStoreResponse (0x56c6f28)->(0x32f158)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x56c6f28)->(0x32f154)
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x52fe770)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x52c5500)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestSucceeded (0x53fad98)->(0x32e874)
fixme:mshtml:on_start_nsrequest OnStartRequest failed: 804b0002
err:mshtml:read_stream_data OnDataAvailable failed: 8000ffff
err:mshtml:read_stream_data buffer is full
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
fixme:wininet:INET_QueryOption Stub for 5
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x4913588)->((null) 1 0x32edb0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 25 2 0x32edc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 26 2 0x32edc4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x4913588)->(0x32ee08)
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32ee9c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32eec4)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 29 2 0x32f834 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x4913588)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x52e0020)->(0x32f248 0x32f234 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4a3ead0)->(0x32f248 0x32f234 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x4e93c60)->(0x32f248 0x32f234 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5271d70)->(0x32f248 0x32f234 0)
fixme:shdocvw:ClientSite_GetContainer (0x4913588)->(0x32f2ac)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x4913588)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 25 2 0x32f1b8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 26 2 0x32f1b8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->((null) 28 2 0x32f8b4 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
fixme:wininet:INET_QueryOption Stub for 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
fixme:wininet:INET_QueryOption Stub for 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
fixme:wininet:INET_QueryOption Stub for 5
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x4a3ea48)->(0x32e9d4)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
fixme:wininet:INET_QueryOption Stub for 5
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x4e93b90)->(0x32e9d4)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x57981c0)->(0x32eed8 0x32eec4 0)
0[1da670]: file wine:https://cashier1.winner.com/payments/Register.php?preview=0&htcmd=1&realmode=1&skin=winnerpoker&language=EN&clienttype=poker&currency=eur&onlinesupport=0&loginplayer=0&casino=winnerpoker&kioskcode=&sessionid=14509375742&remoteip=81.229.156.22&serial=002100b400c3&oldserial=WWW35b9ghm514650&advertiser=&profileid=&bannerid=&gameserver=&gameport=&allowdomain=&lcid=, line 1: ReferenceError: CashierResize is not defined
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5749750)->(0x32eed8 0x32eec4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x4913588)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f4a4)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x559ab48)->(0x32eed8 0x32eec4 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsURI_GetHostPort default action not implemented
wine: Unhandled page fault on read access to 0x00000000 at address 0xfdab44c (thread 0009), starting debugger...
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:INET_QueryOption Stub for 2
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0fdab44c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0fdab44c ESP:0032c0d4 EBP:0032c0d8 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:80000000 EBX:04f77668 ECX:04f77668 EDX:00000000
 ESI:0032c1d0 EDI:0032c7c4
Stack dump:
0x0032c0d4:  0032c0f4 0032c0f8 0fdab2e6 00000000
0x0032c0e4:  80000000 0fda409f 04f77668 034939a0
0x0032c0f4:  0032c114 0032c118 0fda9d62 00000000
0x0032c104:  0032c134 0fd956dc 00000053 00000000
0x0032c114:  04f77668 0032c168 0fd4c423 00000000
0x0032c124:  0032c144 0032c15c 00000000 404f0000
Backtrace:
=>0 0x0fdab44c in js3250 (+0xfb44c) (0x0032c0d8)
  1 0x0fdab2e6 in js3250 (+0xfb2e6) (0x0032c0f8)
  2 0x0fda9d62 in js3250 (+0xf9d62) (0x0032c118)
  3 0x0fd4c423 in js3250 (+0x9c423) (0x0032c168)
  4 0x00aa3eec (0x0032c1b4)
  5 0x0032e7a4 (0x0032e7a4)
  6 0x0fd70b5a in js3250 (+0xc0b5a) (0x0032e7f4)
  7 0x0fcef43d in js3250 (+0x3f43d) (0x0032ea14)
  8 0x0fd021bb in js3250 (+0x521bb) (0x0032eac4)
  9 0x0fcb8391 in js3250 (+0x8391) (0x0032eb04)
  10 0x105ec6e5 in xul (+0x5cc6e5) (0x0032ebc4)
  11 0x1048af8d in xul (+0x46af8d) (0x0032ed04)
  12 0x1048aa7b in xul (+0x46aa7b) (0x0032ede4)
  13 0x1048b23b in xul (+0x46b23b) (0x0032ee24)
  14 0x1048b9d6 in xul (+0x46b9d6) (0x0032ee54)
  15 0x100fc285 in xul (+0xdc285) (0x0032ee84)
  16 0x200f6e21 in mshtml (+0x66e21) (0x0032eeb4)
  17 0x200f8b56 in mshtml (+0x68b56) (0x0032eef4)
  18 0x32b540d8 in urlmon (+0x40d8) (0x0032ef34)
  19 0x32b5481d in urlmon (+0x481d) (0x0032ef54)
  20 0x32b56bd9 in urlmon (+0x6bd9) (0x0032eff4)
  21 0x32b574d8 in urlmon (+0x74d8) (0x0032f044)
  22 0x32b5ac7a in urlmon (+0xac7a) (0x0032f8b4)
  23 0x32b5afa2 in urlmon (+0xafa2) (0x0032f8d4)
  24 0x32b59e95 in urlmon (+0x9e95) (0x0032f934)
  25 0x684bd69a WINPROC_wrapper+0x1a() in user32 (0x0032f964)
  26 0x684bf2fc in user32 (+0x9f2fc) (0x0032f9b4)
  27 0x684c065f in user32 (+0xa065f) (0x0032fa04)
  28 0x68483e7b DispatchMessageW+0x9b() in user32 (0x0032faf4)
  29 0x0049ec08 in casino (+0x9ec08) (0x68483de0)
0x0fdab44c: movl    0x0(%edx),%edx
Modules:
Module    Address            Debug info    Name (187 modules)
PE      340000-  348000    Deferred        xpcom
PE      3d0000-  3f3000    Deferred        gdigraphdriver
PE      400000-  629000    Export          casino
PE     1960000- 1975000    Deferred        nssutil3
PE     1980000- 1a0a000    Deferred        cactivex
PE     1f20000- 1f5b000    Deferred        nspr4
PE     1f60000- 1f6a000    Deferred        plds4
PE     1f70000- 1f7a000    Deferred        plc4
PE     1f80000- 1fa1000    Deferred        smime3
PE     2a60000- 2b76000    Deferred        common
PE     2f90000- 30c0000    Deferred        poker_common
PE     f300000- f5ee000    Deferred        poker_lobby
PE     fcb0000- fdcb000    Export          js3250
PE     fdd0000- fe9b000    Deferred        nss3
PE     fea0000- ff1d000    Deferred        sqlite3
PE     ff20000- ff4a000    Deferred        ssl3
PE    10000000-10017000    Deferred        directsounddriver
PE    10020000-112f8000    Export          xul
PE    122d0000-122e4000    Deferred        npnul32
ELF    20000000-20019000    Deferred        spoolss<elf>
  \-PE    20010000-20019000    \               spoolss
ELF    20019000-2001d000    Deferred        libkeyutils.so.1
ELF    2001d000-2002f000    Deferred        libtasn1.so.3
ELF    2002f000-20043000    Deferred        riched32<elf>
  \-PE    20030000-20043000    \               riched32
ELF    20043000-20084000    Deferred        shdocvw<elf>
  \-PE    20050000-20084000    \               shdocvw
ELF    20084000-20154000    Export          mshtml<elf>
  \-PE    20090000-20154000    \               mshtml
ELF    20154000-201c2000    Deferred        msvcrt<elf>
  \-PE    20160000-201c2000    \               msvcrt
ELF    201c2000-201db000    Deferred        usp10<elf>
  \-PE    201d0000-201db000    \               usp10
ELF    201db000-201f0000    Deferred        dwmapi<elf>
  \-PE    201e0000-201f0000    \               dwmapi
ELF    201f0000-20236000    Deferred        libssl.so.0.9.8
ELF    20236000-20271000    Deferred        rsaenh<elf>
  \-PE    20240000-20271000    \               rsaenh
ELF    21390000-213b0000    Deferred        localspl<elf>
  \-PE    213a0000-213b0000    \               localspl
ELF    290ad000-2913e000    Deferred        crypt32<elf>
  \-PE    290c0000-2913e000    \               crypt32
ELF    29fd9000-2a003000    Deferred        libgssapi_krb5.so.2
ELF    2b791000-2b7ea000    Deferred        riched20<elf>
  \-PE    2b7a0000-2b7ea000    \               riched20
ELF    32b3b000-32b94000    Export          urlmon<elf>
  \-PE    32b50000-32b94000    \               urlmon
ELF    374eb000-374ef000    Deferred        libcom_err.so.2
ELF    39e8b000-39ea0000    Deferred        t2embed<elf>
  \-PE    39e90000-39ea0000    \               t2embed
ELF    406b5000-406bc000    Deferred        libnss_dns.so.2
ELF    45216000-452be000    Deferred        libgnutls.so.26
ELF    4940a000-49550000    Deferred        libcrypto.so.0.9.8
ELF    4b182000-4b264000    Deferred        oleaut32<elf>
  \-PE    4b1a0000-4b264000    \               oleaut32
ELF    50829000-50831000    Deferred        libkrb5support.so.0
ELF    52d2c000-52d4a000    Deferred        libgcc_s.so.1
ELF    543bb000-543cc000    Deferred        libavahi-client.so.3
ELF    557de000-55825000    Deferred        dsound<elf>
  \-PE    557f0000-55825000    \               dsound
ELF    5f8eb000-5f8ff000    Deferred        msimg32<elf>
  \-PE    5f8f0000-5f8ff000    \               msimg32
ELF    62acc000-62b48000    Deferred        libgcrypt.so.11
ELF    65697000-656cd000    Deferred        winspool<elf>
  \-PE    656a0000-656cd000    \               winspool
ELF    67bd6000-67c37000    Deferred        jscript<elf>
  \-PE    67be0000-67c37000    \               jscript
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68158000    Deferred        libwine.so.1
ELF    68158000-68171000    Deferred        libpthread.so.0
ELF    68171000-682b6000    Deferred        libc.so.6
ELF    682b6000-682ba000    Deferred        libdl.so.2
ELF    682ba000-682e0000    Deferred        libm.so.6
ELF    682e0000-682e8000    Deferred        libnss_compat.so.2
ELF    682e8000-682ff000    Deferred        libnsl.so.1
ELF    682ff000-6830a000    Deferred        libnss_nis.so.2
ELF    6830a000-68316000    Deferred        libnss_files.so.2
ELF    68316000-6832f000    Deferred        version<elf>
  \-PE    68320000-6832f000    \               version
ELF    6832f000-68343000    Deferred        lz32<elf>
  \-PE    68330000-68343000    \               lz32
ELF    68343000-68411000    Deferred        comctl32<elf>
  \-PE    68350000-68411000    \               comctl32
ELF    68411000-6851f000    Export          user32<elf>
  \-PE    68420000-6851f000    \               user32
ELF    6851f000-685a9000    Deferred        gdi32<elf>
  \-PE    68530000-685a9000    \               gdi32
ELF    685a9000-68601000    Deferred        advapi32<elf>
  \-PE    685c0000-68601000    \               advapi32
ELF    68601000-68671000    Deferred        rpcrt4<elf>
  \-PE    68610000-68671000    \               rpcrt4
ELF    68671000-6868c000    Deferred        wsock32<elf>
  \-PE    68680000-6868c000    \               wsock32
ELF    6868c000-686b7000    Deferred        ws2_32<elf>
  \-PE    68690000-686b7000    \               ws2_32
ELF    686b7000-686cb000    Deferred        libresolv.so.2
ELF    686cb000-68723000    Deferred        wininet<elf>
  \-PE    686d0000-68723000    \               wininet
ELF    68723000-68739000    Deferred        libz.so.1
ELF    68739000-6875c000    Deferred        mpr<elf>
  \-PE    68740000-6875c000    \               mpr
ELF    6875c000-687ba000    Deferred        shlwapi<elf>
  \-PE    68770000-687ba000    \               shlwapi
ELF    687ba000-6894a000    Deferred        shell32<elf>
  \-PE    687d0000-6894a000    \               shell32
ELF    6894a000-689e7000    Deferred        krnl386.exe16.so
PE    68960000-689e7000    Deferred        krnl386.exe16
ELF    689e7000-689fc000    Deferred        system.drv16.so
PE    689f0000-689fc000    Deferred        system.drv16
ELF    689fc000-68a10000    Deferred        comm.drv16.so
PE    68a00000-68a10000    Deferred        comm.drv16
ELF    68a10000-68a3b000    Deferred        gdi.exe16.so
PE    68a20000-68a3b000    Deferred        gdi.exe16
ELF    68a3b000-68a62000    Deferred        libexpat.so.1
ELF    68a62000-68aa4000    Deferred        user.exe16.so
PE    68a70000-68aa4000    Deferred        user.exe16
ELF    68aa4000-68ab9000    Deferred        display.drv16.so
PE    68ab0000-68ab9000    Deferred        display.drv16
ELF    68ab9000-68ace000    Deferred        keyboard.drv16.so
PE    68ac0000-68ace000    Deferred        keyboard.drv16
ELF    68ace000-68ae2000    Deferred        mouse.drv16.so
PE    68ad0000-68ae2000    Deferred        mouse.drv16
ELF    68ae2000-68b81000    Deferred        winex11<elf>
  \-PE    68af0000-68b81000    \               winex11
ELF    68b81000-68b8a000    Deferred        libsm.so.6
ELF    68b8a000-68ba5000    Deferred        libice.so.6
ELF    68ba5000-68cd4000    Deferred        libx11.so.6
ELF    68cd4000-68cd9000    Deferred        libuuid.so.1
ELF    68cd9000-68cdd000    Deferred        libxau.so.6
ELF    68cdd000-68cfb000    Deferred        libxcb.so.1
ELF    68cfb000-68d1c000    Deferred        imm32<elf>
  \-PE    68d00000-68d1c000    \               imm32
ELF    68d1c000-68d1f000    Deferred        libxinerama.so.1
ELF    68d1f000-68d25000    Deferred        libxxf86vm.so.1
ELF    68d25000-68d2f000    Deferred        libxrender.so.1
ELF    68d2f000-68d38000    Deferred        libxrandr.so.2
ELF    68d38000-68d3c000    Deferred        libxcomposite.so.1
ELF    68d3c000-68d42000    Deferred        libxfixes.so.3
ELF    68d42000-68d4d000    Deferred        libxcursor.so.1
ELF    68d4d000-68d80000    Deferred        uxtheme<elf>
  \-PE    68d50000-68d80000    \               uxtheme
ELF    68d80000-68e7d000    Deferred        ole32<elf>
  \-PE    68da0000-68e7d000    \               ole32
ELF    68e7d000-68eb4000    Deferred        winealsa<elf>
  \-PE    68e90000-68eb4000    \               winealsa
ELF    68eb4000-68f7b000    Deferred        libasound.so.2
ELF    68f7b000-68f84000    Deferred        librt.so.1
ELF    68f87000-68fc7000    Deferred        libpulse.so.0
ELF    68fc7000-69011000    Deferred        libpulsecommon-0.9.19.so
ELF    69011000-69017000    Deferred        libxtst.so.6
ELF    69017000-69020000    Deferred        libwrap.so.0
ELF    69020000-6908c000    Deferred        libsndfile.so.1
ELF    6908c000-690c5000    Deferred        libdbus-1.so.3
ELF    690c5000-691c1000    Deferred        libvorbisenc.so.2
ELF    691c1000-691ea000    Deferred        libvorbis.so.0
ELF    691ea000-691f1000    Deferred        libogg.so.0
ELF    691f1000-691f8000    Deferred        libasound_module_pcm_pulse.so
ELF    691f8000-69210000    Deferred        msacm32<elf>
  \-PE    69200000-69210000    \               msacm32
ELF    69210000-69236000    Deferred        msacm32<elf>
  \-PE    69220000-69236000    \               msacm32
ELF    69236000-6924c000    Deferred        midimap<elf>
  \-PE    69240000-6924c000    \               midimap
ELF    6fa25000-6fa35000    Deferred        libxext.so.6
ELF    70115000-70135000    Deferred        iphlpapi<elf>
  \-PE    70120000-70135000    \               iphlpapi
ELF    708b3000-7095e000    Deferred        comdlg32<elf>
  \-PE    708c0000-7095e000    \               comdlg32
ELF    74b24000-74b29000    Deferred        libxdmcp.so.6
ELF    74fd1000-74ff8000    Deferred        netapi32<elf>
  \-PE    74fe0000-74ff8000    \               netapi32
ELF    758d4000-75979000    Deferred        libkrb5.so.3
ELF    75d1e000-75d47000    Deferred        libk5crypto.so.3
ELF    783a1000-783ad000    Deferred        libavahi-common.so.3
ELF    78f66000-78fe5000    Deferred        libfreetype.so.6
ELF    7933c000-79340000    Deferred        libnss_mdns4_minimal.so.2
ELF    7a286000-7a2b3000    Deferred        libfontconfig.so.1
ELF    7a796000-7a7db000    Deferred        libcups.so.2
ELF    7ac3d000-7ac8d000    Deferred        libflac.so.8
ELF    7b2f3000-7b37a000    Deferred        winmm<elf>
  \-PE    7b300000-7b37a000    \               winmm
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb5000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb5000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7ceee000-7cef3000    Deferred        libgpg-error.so.0
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\danne\.wine\dosdevices\c:\Poker\Winner Poker\casino.exe
    00000028    0
    00000024    0
    00000026    0
    00000025    0
    00000013    0
    00000012    0
    00000011    0
    00000016    0
    0000001a    0
    0000001b    0
    00000017    0
    00000019    0
    00000018    0
    00000047    0
    00000044    0
    0000003f    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000035    0
    00000034    0
    00000033   -1
    00000032   -1
    00000031    0
    00000030   -1
    0000002f   -1
    0000002e    0
    0000002d   -1
    0000002c   -1
    0000002b   15
    0000002a    1
    00000027   -2
    00000023    0
    00000009    0 <==
0000000c services.exe
    0000003d    0
    0000001f    0
    0000000e    0
    0000000d    0
0000000f explorer.exe
    00000010    0
0000001c winedevice.exe
    00000022    0
    00000021    0
    0000001e    0
    0000001d    0
Backtrace:
=>0 0x0fdab44c in js3250 (+0xfb44c) (0x0032c0d8)
  1 0x0fdab2e6 in js3250 (+0xfb2e6) (0x0032c0f8)
  2 0x0fda9d62 in js3250 (+0xf9d62) (0x0032c118)
  3 0x0fd4c423 in js3250 (+0x9c423) (0x0032c168)
  4 0x00aa3eec (0x0032c1b4)
  5 0x0032e7a4 (0x0032e7a4)
  6 0x0fd70b5a in js3250 (+0xc0b5a) (0x0032e7f4)
  7 0x0fcef43d in js3250 (+0x3f43d) (0x0032ea14)
  8 0x0fd021bb in js3250 (+0x521bb) (0x0032eac4)
  9 0x0fcb8391 in js3250 (+0x8391) (0x0032eb04)
  10 0x105ec6e5 in xul (+0x5cc6e5) (0x0032ebc4)
  11 0x1048af8d in xul (+0x46af8d) (0x0032ed04)
  12 0x1048aa7b in xul (+0x46aa7b) (0x0032ede4)
  13 0x1048b23b in xul (+0x46b23b) (0x0032ee24)
  14 0x1048b9d6 in xul (+0x46b9d6) (0x0032ee54)
  15 0x100fc285 in xul (+0xdc285) (0x0032ee84)
  16 0x200f6e21 in mshtml (+0x66e21) (0x0032eeb4)
  17 0x200f8b56 in mshtml (+0x68b56) (0x0032eef4)
  18 0x32b540d8 in urlmon (+0x40d8) (0x0032ef34)
  19 0x32b5481d in urlmon (+0x481d) (0x0032ef54)
  20 0x32b56bd9 in urlmon (+0x6bd9) (0x0032eff4)
  21 0x32b574d8 in urlmon (+0x74d8) (0x0032f044)
  22 0x32b5ac7a in urlmon (+0xac7a) (0x0032f8b4)
  23 0x32b5afa2 in urlmon (+0xafa2) (0x0032f8d4)
  24 0x32b59e95 in urlmon (+0x9e95) (0x0032f934)
  25 0x684bd69a WINPROC_wrapper+0x1a() in user32 (0x0032f964)
  26 0x684bf2fc in user32 (+0x9f2fc) (0x0032f9b4)
  27 0x684c065f in user32 (+0xa065f) (0x0032fa04)
  28 0x68483e7b DispatchMessageW+0x9b() in user32 (0x0032faf4)
  29 0x0049ec08 in casino (+0x9ec08) (0x68483de0)
fixme:shdocvw:WebBrowser_Stop (0x1fee90)
fixme:wininet:INET_QueryOption Stub for 5
fixme:shdocvw:WebBrowser_Stop (0x20d5d8)

```


Then the client just crashed.

---

### Post by jaansson on 2010-02-03
Just figured out one way to do it:

Start Winner through the terminal with that iexplorer thing.
Click the Register Account button.
When the client crashes, look in the terminal for a http adress.
Paste it in Firefox and there you go, the cashier window, and you can register an account.

It's probably the same with all IPoker clients.

Would still be great to know how to make iexplorer work in the clients though :)

---

### Post by ellgor on 2010-02-03
Hi,

If you want to play online poker I can recommend Coral Poker, you dont need special apps or anything, their instant play really is (assuming your fully upto-date with your distro).

Regards, Ellgor.

---

### Post by jaansson on 2010-02-04
Thanks for the tip ellgor.

I'd really prefer to play at Winner though, since I've heard it's good. But if I can't figure it out, I might check it out :)

---

